# GitHub Clone with Bootstrap 4
## Set up
1. Create a `index.html` file.
2. Include the Bootstrap CDN links:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.1/css/bootstrap.min.css" integrity="sha384-VCmXjywReHh4PwowAiWNagnWcLhlEJLA5buUprzK8rxFgeH0kww/aWY76TfkUoSX" crossorigin="anonymous">
    <title>GitHub Clone</title>
</head>
<body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.1/js/bootstrap.min.js" integrity="sha384-XEerZL0cuoUbHE4nZReLT7nx9gQrQreJekYhJD9WNWhH8nEW+0c5qq7aIo2Wl30J" crossorigin="anonymous"></script>
</body>
</html>
```
## Navbar
3. Create a `header` tag.
4. Copy code example for responsive navbar *with a brand name shown on the left and toggler on the right* and paste it between the `header` tag - [get code example](https://getbootstrap.com/docs/4.5/components/navbar/#responsive-behaviors)

5. With this example the `button` is hidden at mobile size, in the GitHub website it is shown, so to fix this copy the `form` block and paste it after the first `a` tag.
```html
...
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Navbar</a>
    <form class="form-inline my-2 my-lg-0 d-lg-none ml-auto mr-3">
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Sign Up</button>
    </form>
...
```
6. Now the button shows at any screen size and is centred, which we don't want. Change the form to the following:
```html
<form class="form-inline my-2 my-lg-0 d-lg-none ml-auto mr-3">
    <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Sign Up</button>
</form>
```
`d-lg-none` will hide on screens wider than lg [Display property](https://getbootstrap.com/docs/4.0/utilities/display/)

`ml-auto` sets the left margin to auto.

`mr-3` set margin right to 1rem - [Spacing](https://getbootstrap.com/docs/4.0/utilities/spacing/#notation)
### Drop down links
7. Change links to drop down link. Replace the first `li` tag with the following:
```html
<li class="nav-item dropdown">
    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Dropdown
    </a>
    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
        <a class="dropdown-item" href="#">Action</a>
        <a class="dropdown-item" href="#">Another action</a>
        <div class="dropdown-divider"></div>
        <a class="dropdown-item" href="#">Something else here</a>
    </div>
</li>
```
8. To look more like GitHub change to the following:
```html
<div class="dropdown-menu" aria-labelledby="navbarDropdown">
    <a href="#" class="dropdown-item">Code review</a>
    <a href="#" class="dropdown-item">Project management</a>
    <a href="#" class="dropdown-item">Integrations</a>
    <a href="#" class="dropdown-item">Actions</a>
    <a href="#" class="dropdown-item">Packages</a>
    <a href="#" class="dropdown-item">Security</a>
    <a href="#" class="dropdown-item">Team management</a>
    <a href="#" class="dropdown-item">Hosting</a>
    <div class="dropdown-divider"></div>
    <a href="#" class="dropdown-item">Customer stories</a>
    <a href="#" class="dropdown-item">Security</a>
</div>
```
9. Create a `style.css` file and add the following:
```css
.dropdown-menu{
    display: none;
	width: 300px;
	border-radius: 6px;
    padding: 24px;

    animation: dropdown-display .4s cubic-bezier(.73,.005,.22,1);
    animation-duration: 0.4s;
    animation-timing-function: cubic-bezier(0.73, 0.005, 0.22, 1);
    animation-delay: 0s;
    animation-iteration-count: 1;
    animation-direction: normal;
    animation-fill-mode: none;
    animation-play-state: running;
    animation-name: dropdown-display;
}
.dropdown-item{
    padding-left: 0;
}
@keyframes dropdown-display{
    0% {
        opacity: 0;
        transform: scale(.98) translateY(-.6em);
    }
    100% {
        opacity: 1;
        transform: scale(1) translateY(0);
    }
}
```
#### Show drop down link on hover
10. At the bottom of `index.html` add the following:
```html
<!-- Custom js -->
<script>
    /* Bootstrap Dropdown with Hover */
    /* https://stackoverflow.com/questions/16214326/bootstrap-dropdown-with-hover */
    $('.dropdown').hover(function(){ 
        $('.dropdown-toggle', this).trigger('click'); 
    });
</script>
```
#### Add octocat
11. In `style.css` add the following to the top:
```css
.text-white {color:#fff;}
.octicon {fill: currentColor;}
```
12. In `index.html`, replace the first `a` tag with the following:
```html
<a class="navbar-brand" href="#">
    <svg height="32" class="octicon octicon-mark-github text-white" viewBox="0 0 16 16" version="1.1" width="32" aria-hidden="true"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path></svg>
</a>
```
### Change links text to white
13. In `style.css` add the following:
```css
.navbar-dark .navbar-nav .nav-link {color:#fff}
```
### Make sign up button visible
14. In `index.html`, on both of the sign up buttons, add the a class name called `btn-outline-custom`. In `style.css` add the following:
```css
.btn-outline-custom {color: #fff;border: 1px solid #e1e4e8;}
.btn-outline-custom:hover {color: #fff; opacity: .75;}
```
### Remove outline on dropdown links
15. In `style.css` add the following:
```css
:focus {
    outline: -webkit-focus-ring-color none;
}
```
### Give search input a grey background with visible text
16. In `style.css` add the following:
``` css
.form-control{background-color: hsla(0,0%,100%,.125); border: none}
.form-control::-webkit-input-placeholder {
    color: hsla(0,0%,100%,.7);
}
```
### Reset hover colour on dropdown links
17. In `style.css` add the following:
```css

#navbarDropdown:hover {color: rgba(255,255,255,.75);}
#navbarDropdown1:hover {color: rgba(255,255,255,.75);}
#navbarDropdown2:hover {color: rgba(255,255,255,.75);}
#navbarDropdown:not(:hover){color: #fff;}
#navbarDropdown1:not(:hover){color: #fff;}
#navbarDropdown2:not(:hover){color: #fff;}
```
