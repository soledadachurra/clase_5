# Clase 5 → Miércoles 4 de abril

### JS: JavaScript

JavaScript es un lenguaje de programación. Como tal, tiene su sintaxis, semántica y usos.

JavaScript es usado para crear interactividad dinámica en web. Para ello, puede ser incluido o vinculado a documentos HTML: 

- incluido entre etiquetas `<script>javascript</script>`

- vinculado, como atributo, en la primera de las mismas etiquetas `<script src="javascript.js"></script>`

Lo que se incluya o se vincule, puede tener una estructura tan sencilla como la que sigue: 

```
function lifeOfPi() {
    alert(Math.PI);
}
```
Luego, en el mismo HTML donde tal código es incluido o vinculado, puedo escribir:

`<button onclick="lifeOfPi()">Alerta</button>`

Con ello, cada vez que "interactúe" con ese botón, dándole un clic, se desplegará un mensaje de alerta en mi navegador, donde se podrá leer 3.141592653589793

En ese ejemplo, brevísimo, ya estoy [creando una función](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Funciones), y aprovechando un [objeto relacionado con cálculos matemáticos](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/), además de aprovechar el método que [despliega alertas del navegador](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_alert2). 

Desde este punto se puede crecer mucho. Para ello es muy conveniente apoyarse en referencias que se pueden encontrar en línea. Referencias tales como:

- [Fundamentos de JavaScript](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

- [Referencias de JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia)

- [JavaScript for Beginner](http://xahlee.info/js/js_basics_index.html)

- [JavaScript Tutorial](https://www.w3schools.com/js/)

- [JavaScript.com](https://www.javascript.com/learn/javascript/strings)

En lo que sigue, y durante esta clase, vamos a armar las bases trabajar con datos en JavaScript.

#### Variables en JavaScript 

Hasta la asignación de un valor por almacenar, todas las variables en Javascript se crean de la misma forma. Primero `var`, luego un nombre para identificarla y después la asignación `=` del valor que corresponda almacenar en ella. Lo que sigue después del signo igual dependerá del tipo de valor que se almacene:

Para un valor entero (integer) o un valor de punto flotante (float), después de la asignación (=) se ingresa solamente el número. `var a = 618; var b = 3.14159265359;`

Para una cadena de caracteres (string), después de la asignación (=) se agregan comillas dobles o simples, delimitando comienzo y final de la cadena: `var c = " "; var d = "Hola mundo!";`

Para un booleano o variable de tipo lógico, después de la asignación (=) se ingresa la palabra true o false. `var d = true; var e = false;` en este caso no se usan las comillas. De usarlas, el programa pensaría que se está almacenando una cadena de caracteres.

Para un arreglo (array), después de la asignación (=) se agregan paréntesis cuadrados, delimitando comienzo y final del conjunto. `var primos = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29];` luego, lo que sea parte del arreglo puede ser identificado por su posición, correspondiendo `primos[0]` al 2 que está en la primera posición, `primos[1]` al 3 que está en la segunda, y así sucesivamente.

Para un objeto (object), después de la asignación (=) se agregan paréntesis de llave, delimitando comienzo y final de un conjunto de pares. En cada par, lo primero denomina a lo que se almacena en el segundo (siguiendo las reglas ya definidas).

```
var auto = {
precio: 11490000,
modelo: "Nissan Kicks Advance MT", 
disponible: true, 
versiones: [2019,2018,2017]
};
```

A un objeto le podemos pedir cada cosa por su nombre. Así, por ejemplo, `auto.precio` es 11490000, `auto.disponible` es true, y `auto.versiones[0]` es 2019. Noten como en el último caso se pide el primer elemento del arreglo denominado versiones, dentro del objeto auto.

### JSON

Inmediatamente después de presentar a las variables que contienen objetos en JavaScript, podemos hablar de JSON (JavaScript Object Notation). Este es un formato ligero de intercambio de datos. Debido a su amplia adopción como alternativa a XML (eXtensible Markup Language), se considera un formato de lenguaje independiente. Muchos datos son compartidos en JSON. Algunos ejemplos:

- How Many People Are In Space Right Now: http://api.open-notify.org/astros.json

- Current Location of the International Space Station: http://api.open-notify.org/iss-now.json

- Darth Vader @ SWAPI: https://swapi.co/api/people/4/?format=json

Antes de hacer clic en los vínculos a ejemplos, se recomienda instalar una extensión en sus navegadores: En Chrome podrían instalar [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc) o [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa).

También conviene mencionar a GeoJSON, un derivado de JSON, que es ampliamente utilizado en aplicaciones de cartografía en entornos web al permitir el intercambio de datos de manera rápida, ligera y sencilla. A diferencia de otros estándares SIG, no está desarrollado y mantenido por una organización oficial, sino que es mantenido por una comunidad de desarrolladores en Internet.

En la clase de hoy trabajaremos, primero, con un GeoJSON, y después trabajaremos con dos APIs que nos entregarán datos en formato JSON. En todos los casos usaremos el siguiente script para consultarlos:

```
var request = new XMLHttpRequest();
request.open('GET', 'URI', true);
request.onload = function () {
	var data = JSON.parse(this.response);
	//acá agregaremos más…
}
request.send();
```

**¡Un parche antes de la herida!**

Hay un problema que nos podríamos encontrar al consultar un JSON en una URL que comienza con `http://` y después intentar ver el resultado en un documento HTML en URL que empiece con `https://`

El problema sería un "[Mixed Content](https://developer.mozilla.org/es/docs/Seguridad/MixedContent/arreglar_web_con_contenido_mixto)". Para saltarnos eso, en algunas URL voy a aprovechar el servicio de [crossorigin.me](https://crossorigin.me/). Por eso podrían encontrarán un "request" raro, donde la URL diría, por ejemplo, `https://crossorigin.me/http://api.open-notify.org/iss-now.json`

- - - - - 

[Clase anterior](https://github.com/profesorfaco/dno037-2018-04) | [Siguiente clase](https://github.com/profesorfaco/dno037-2018-06)
