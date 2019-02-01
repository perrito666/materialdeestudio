# Terminal y comandos

## Notas del autor
(Los ejemplos a continuación son dados utilizando la terminal por omisión de macos o [iTerm](https://www.iterm2.com/))

Muchos de los conceptos vertidos aqui son introductorios y carecen de detalle al punto de parecer erroneos al ojo experto, téngase en cuenta que este texto tiene como finalidad introducir al uso directo de las herramientas descriptas y no es un compendio de conocimiento detallado sobre terminales

## Introducción

La terminal o consola (dos terminos utilizados indistintamente en español actualmente para referirse a lo mismo) es una abstracción del sistema de nuestra computadora.

Típicamente, los usuarios modernos estan acostumbrados a abstracciones mas gráficas de los programas de la computadora, tales como íconos, interfaces visuales (lo que se ve de cualquier programa) componentes animados, etc.

Explicado de una manera cruda (y arbitraria en las separaciones), una computadora funcional de la siguiente manera:

| Componente | Descripción |
| ---------- | ----------- |
| Aplicacion | Una aplicación es probablemente la parte de nuestro modelo que menos explicaciones requerirá, es un programa que, típicamente, es lanzando y controlado por el usuario e interactua con el mismo, ejemplos típicos de esto son faciles de conseguir ya que desde el navegador hasta el editor de texto son aplicaciones, a estas mismas nos referiremos mas adelante cuando exploremos las aplicaciones CLI (Interface de linea de comando, por sus siglas en Inglés) que son aquellas con las que el usuario típico puede estar mucho menos familiarizado ya que carecen de una interface gráfica (GUI) tal como las antes mencionadas |
| Shell | El shell, es la capa (que a eso hace alusion su numbre) que recubre al sistema operativo y abstrae sus partes mas complicadas para que el usuario puede hacer uso de las mismas, en la actualidad lo mas comun es tener un Shell gráfico. Ejemplos de Shell gráfico es "lo que vemos" cuando utilizamos windows o macos o incluso versiones modernas y orientadas a usuarios generales de GNU/Linux. Típicamente los shells gráficos corren directamente sobre el sistema operativo aunque en algunos sistemas operativos hay un shell de texto sobre el cual corre la interface gráfica que puede ser una aplicación |
| sistema operativo | Es un conjunto de aplicaciones de bajo nivel que, en conjunto con el kernel interactuan con los aspectos varios del hardware, aqui encontraremos cosas como los sistemas de archivos, los drivers que nos indican como controlar dispositivos, etc. |
| hardware | Todo aquello que podemos patear |

## La interface grafica
El uso típico de la computadora moderna, nos presenta un "Entorno gráfico" abreviado típicamente como GUI por sus siglas en Inglés (Graphical User Interface) que nos muestra un "Escritorio" que es la vista de una carpeta homónima que contiene "Iconos" que bien pueden ser de "Aplicaciones" o "Archivos Comunes" comunmente utilizaremos dichos íconos u otros que se encuentren en los diversos menus para lanzar aplicaciones y utilizaremos un explorador de archivos para poder encontrar y ejecutar acciones sobre nuestros archivos comunes.

La realidad es que la GUI es simplemente una abstración sobre la estructura algo mas simple que se encuentra debajo. En nuestro modelo de capaz, la GUI seria el Shell. Quienes han tenido la oportunidad de utilizar varios sistemas operativos (por ejemplo el del teléfono en contraste del de la computadora) Habran notado que la elección de las abstraciones visuales no es la misma en cada uno y en general se adaptan al medio o al paradigma reinante (durante los años la forma preferida de representar archivos y programas ha variado por gusto, evolución de la comprensión de las costumbres del usuario y posibilidades técnicas).

## La interface de texto
La CLI (Comand Line Interface) comunmente referida como "Terminal" o "Consola" o quizas no tan comunmente "Linea de comandos" es otra forma de representación visual de los archivos y aplicaciones dentro de una computadora, quizas puede resultar mas chocante por su diferencia abismal de paradigma. Si bien esta forma es una de las mas antiguas (predata el hecho de que las computadoras tengan terminal) sigue aun vigente, mas que nada, por la expresividad y versatilidad que permite al usuario. Es simplemente, otra forma de Shell.

Una de las formas mas faciles de aproximarse a la terminal como concepto, es su nombre ya no tan comun (al menos en Español) "Linea de comandos" que hace alusión al hecho de que siempre se nos presenta con una linea en la que esta el cursor y en la que podremos tipear comandos. Todo aquello que no es la proverbial linea es simplemente la forma del CLI de presentarnos datos.


## Terminales modernas
En su uso mas moderno, ya hablando exclusivamente de las versiones de Unix (macos, linux, iOS, otros menos populares) lo que en general accedemos son "Emuladores de terminal". No viene al caso los mecanismos que operan por debajo de la misma, pero basta con denotar que es una Aplicación que corre en la GUI que habitualmente usamos y que nos permite acceder a nuestro sistema operativo de la misma manera que un Shell tipico de texto nos permitiria (o sea, de la misma forma que si la computadora en lugar de enviarnos a la interface grafica nos presentara con la linea de comandos como unica capa sobre el sistema operativo)

## Uso típico de la CLI
En todas o al menos la mayoria de las terminales, se nos presnetará una linea en la que podemos ejecutar comandos y aplicaciones, antes de embarcarnos en el tema algunas consideraciones generales que quizas nunca hayamos notado y son en este momento mas importantes que nunca.

* Mayusculas Y Minusculas: En la mayoria de los casos, excepto por algunas versiones de windows y algunas configuraciones posibles de macos, la computadora no entiende las mayusculas y minúsculas como lo mismo (en su representacion interna son dos cosas distintas) por lo cual es importante prestar especial atención a los comandos y nombres de archivos a la hora de utilizar la consola
* Los espacios y caracteres no comunes (fuera de `A-Za-Z0-9,._`) a veces tienen significados especiales por lo tanto deberán ser "escapados" esto se logra anteponiendo `\` a dicho caracter por ejemplo `un\ archivo.txt` significa que me estoy refiriendo a un archivo cuyo nombre es `un archivo.txt` y no que estoy refiriendomen a dos cosas distintas llamadas respectivamente `un` y `archivo.txt` mas adelante esto tendrá mas sentido pero es una buen punto a tener en cuenta para cuando veamos la barra invertida.
* Los paths: En la típica representación visual de la estructura de archivos que vemos en la diaria hay un arbol de directorios que navegamos con la flecha del mouse y nuestro navegador de archivo nos muestra sobre el area donde se ven los archivos que contiene el actual directorio. En un Finder de macos veremos que la barra de título dice algo como `/Volumenes/Macintosh HD/Users/horacio/...` y así y en windows `> This PC > Documentos` o `C:\\Users\horacio\Documentos` En un CLI esto se representa, en unix al menos, con nombres de Carpetas separados por `/` siendo la raiz de todo simplemente la primer `/` en donde todo esta guardado (hay conceptos mas complejos involucrados pero no vienen al caso ahora) es muy probable que la terminal que usemos nos muestre una parte parcial de este path o ruta para orientarnos.

## Comenzando
Cuando abrimos una nueva ventana la terminal nos presentará el "prompt" que es la antes mencionada linea de comandos en la que podremos escribir comandos para que esta terminal interprete.
La primer palabra que escribamos sera aquello que la terminal interprete como "comando" y las siguientes seran los "parámetros" informacion que el comando utilizará para modificar su ejecución, esto quedará mas claro en ejemplos mas adelante.
¿Que es un comando? Vale la pena explicarlo, un comando, desde el punto de vista del CLI es probablemente una de tres cosas:

* Un comando interno del shell: hay palabras clave que el shell entenderá como comandos y actuara acorde para modificarse a si mismo o a nustro entorno
* Un binario ejecutable: Un archivo, comun y corriente, que tiene como caracteristica ser "ejecutable" para usuarios sasonados de windows esto seria un `.exe` las Aplicaciones que corremos gráficamente suelen ser esto, un binario que la GUI nos muestra (recordemos que comunmente vemos Iconos para las aplicaciones y para los archivos comunes pero en general solo cambia el dibujo del ícono).
* Un script: Un archivo de texto con comandos en algun lenguaje "interpretado" lease cuyos ejecutables son simplemente una lista de comandos que una aplicacion correrá en orden 

La terminal utiliza algo de información comun para saber que comandos tiene disponibles en terminos de "aplicaciones" (las aplicaciones en nuestro sistema operativo, tanto con como sin interface grafica estan guardadas en carpetas especiales en las que los Shells buscaran para presentarnoslos como comandos posibles, es posible ejecutar aplicaciones por fuera de estos pero sera cubierto en otro documento)

Entonce comenzaremos escribiendo algunos comandos y ejecutandolos a traves de la tecla "Enter" (o "Return" si su teclado es en Inglés)

## Navegacion por el sistema de archivos
La CLI tiene el mismo concepto que la GUI nos muestra como escritorio, pero de una forma algo mas cruda. Si bien no es evidente, apenas inciamos una Terminal nos encontramos en lo que se denomina "el home" que es una carpeta en nuestra computadora donde estan todos nuestros archivos (es la carpeta que contiene al escritorio por ejemplo) y tenemos varios comandos disponibles para "movernos" dentro de estas estructuras y ver sus contenidos asi como operar sobre los mismos, a continuacion veremos algunos ejemplos prácticos.

Cada comando que ejecutemos puede o no imprimir algo y terminara ofreciendonos una nueva linea de comandos para continuar operando, la mayoria de las terminales tienen bastante historia hacia arriba para poder ver comandos pasados y la información que imprimieron. El uso de la terminal puede recordarnos a una sumadora mecánica en este aspecto y es porque en su origan funcionaba así, predatando a los monitores las terminales eran impresoras y los comandos y sus resultados simplemente se imprimian en papel. Como regla memotécnica se agrega el significado mas probable del comando

* `pwd` este comando imprimirá el directorio actual, es algo muy util si nustra terminal no muestra el mismo antes del prompt. `print working directory` es su raiz probable.
* `ls` este comando imprime los contenidos de la carpeta actual. probablemente abrevia `list` 
* `cd` sin ningun argumento este comando cambiara a la carpeta home del usuario pero podemos darle argumentos para que nos lleve a una carpeta, ejemplos a continuacion (el significado probable es  `change directory`)
  * `cd Documents` cambiará a la carpeta `Documents` si esta existiera dentro del directorio actual.
  * `cd /home/horacio/Documents` cambiará a la carpeta `Documents` del home de horacio sin importar donde nos encontremos porque le hemos dado el Path completo (recordemos que `/` es la raiz de todo, así pues si pasamos la ruta completa del directorio `cd` hara caso omiso del directorio actual)

Veamos un ejemplo corto de navegación.

```bash
$ pwd
/home/horacio
$ ls 
Desktop    Videos
Documents  holaquetal.txt
Pictures
$ cd Desktop
$ pwd
/home/horacio/Desktop
$ cd Documents
 cd: Documents: No such file or directory
$ cd /home/horacio/Documents
$ pwd
/home/horacio/Documents
```

En este caso toda la navegación fue hecha con comandos, no binarios ejecutables ni scripts porque todos los movimientos dentro del sistema de directorios son comandos propios del shell que esta, a fin de cuentas, interactuando con el disco rígido a traves del sistema operativo.

