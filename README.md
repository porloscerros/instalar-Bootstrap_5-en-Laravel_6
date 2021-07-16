Repositorio de ejemplo con los pasos para instalar Bootstrap 5 en un Proyecto hecho en Laravel 6.

Referente a esta pregunta de SOEs:  
[¿Cómo instalar Bootstrap5 en Laravel 6?](https://es.stackoverflow.com/questions/468964/c%c3%b3mo-instalar-bootstrap5-en-laravel-6?noredirect=1#comment835700_468964).


---------------------------

Creas un proyecto Laravel en la versión 6:

    composer create-project --prefer-dist laravel/laravel blog "6.*"
    
Y lo levantas con:

    php artisan serve
    
Esto iniciará un servidor de desarrollo en [http://localhost:8000](http://localhost:8000), donde podrás ver la página de bienvenida de Laravel 6.

Luego instalas las dependencias de front-end y las compilas:

    npm install
    npm run dev
    
A continuación instalas Bootstrap:

    npm install bootstrap @popperjs/core --save-dev
    
Dentro del directorio `resources/scss/` modifica el archivo `app.scss` para importar los estilos:

    // resources/scss/app.scss 
    
    @import "~bootstrap/scss/bootstrap";
    
Dentro del directorio `resources/js/` modifica el archivo `bootstrap.j`s para importar el módulo de js:

    // resources/js/bootstrap.js 
    
    window._ = require("lodash");
    import "bootstrap";
    //...
    
Vuelve a compilar:

    npm run dev
    
Modifica la vista de bienvenida que trae laravel para cargar el js y los estilos compilados:

    <!DOCTYPE html>
    <html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1">
    
            <title>Laravel 6 y Bootstrap 5</title>
    
            <link href="{{ mix('css/app.css') }}" rel="stylesheet">
        </head>
        <body>
    
    
        <script src="{{ mix('/js/app.js') }}"></script>
        </body>
    </html>
    
Pronto, ya tienes Bootstrap 5 instalado y funcionado. Puedes agregar el html con las clases de Bootstrap 5.
