---
layout: post
title:  "Principios de Arquitectura"
date:   2017-10-18 12:26:00 +0000
categories:
---

La arquitectura de software se encuentra principalmente relacionada a cómo se definen los bloques de construcción (módulos, componentes, clases, procedimientos, etc.) de un sistema y cómo interactúan entre ellos. Las arquitecturas representan diferentes variantes de los atributos de calidad de sus sistemas y, aunque es difícil decir que una arquitectura es "buena" o "mala", existen principios generales que se deben considerar cuando se diseña una arquitectura. Estos principios se centran en dos problemas principales: **reducir la complejidad** e **incrementar la flexibilidad (o facilidad de modificar)** una arquitectura.
A continuación se muestra una lista de los principios de arquitectura:

1. **Bajo Acoplamiento**
2. **Alta Cohesión**
3. **Diseño para el Cambio**
4. **Separación de Intereses**
5. **Ocultamiento de la Información**
6. **Abstracción**
7. **Modularidad**
8. **Trazabilidad**
9. **Auto-documentación**
10. **Incrementalidad**

## 1. **Bajo Acoplamiento**
El acoplamiento es la relación entre los bloques de construcción (módulos, componentes, clases, procedimientos, etc.) de una arquitectura de software.

A continuación se muestran tres ejemplos de acoplamiento (hay muchos más tipos) ordenados del más fuerte al menos fuerte:
  - Las clases pueden acceder mutuamente a sus datos (privados). De esta forma no puedes cambiar alguna de las clases sin considerar la otra.
  - Las clases se comunican mediante una estructura global de datos. Las dependencias directas entre las clases reside en la estructura global de datos. A pesar de esto, el acoplamiento aún es algo fuerte: todos lo cambios que afectan los datos globales también afectan todas las clases que funcionan con los datos.
  - Las clases solo se comunican mediante parámetros de métodos, el acoplamiento es considerablemente más bajo: los métodos involucrados contienen solo datos esenciales. Los cambios en este acoplamiento de datos, por lo tanto, solo provocan cambios locales en los métodos relevantes de las clases involucradas.

### Principio de Bajo Acoplamiento
Este principio establece que el acoplamiento entre los bloques de construcción deben mantenerse tan bajo como sea posible.
Este principio tiene dos objetivos:
1. Mantener baja la complejidad de las estructuras:
  "Es más fácil entender el bloque de construcción sin tener que entender un montón de otros bloques"

2. Incrementar la facilidad de modificación de la arquitectura:
  "Cuantos menos bloques de construcción son afectados por un cambio en otro bloque (debido al fuerte acoplamiento) y cuantas menos relaciones existan más fácil es hacer cambios localmente en los bloques de construcción"

### Enlaces útiles
- "No hables con extraños": Ley de Demeter
- Evita dependencias circulares
- "No nos llames, nosotros te llamamos": Principio de Hollywood (Inversión de Control)
- Inversión de dependencias
- Inyección de dependencias

## 2. **Alta Cohesión**
El principio de bajo acoplamiento se preocupa de las dependencias entre diferentes bloques de construcción de una arquitectura. El principio de alta cohesión se preocupa de las dependencias entre las distintas partes de cada bloque de construcción. La cohesión es una medida de qué tan auto-contenido se encuentra un bloque de construcción, semánticamente.

Con referencia a los métodos de una clase, la cohesión se puede medir mediante las llamadas que se hacen uno al otro. En tiempo de ejecución sería que, el objeto _x_ tiene alta cohesión si éste se llama a sí mismo frecuentemente.

### Principio de Alta Cohesión
La cohesión dentro de un bloque de construcción de un sistema debe ser tan alta como sea posible. Además, la alta cohesión tiene una fuerte relación con el bajo acoplamiento: "Entre más alta sea la cohesión de los bloques de construcción individuales en una arquitectura, más bajo es el acoplamiento entre los bloques de construcción".

Puedes lograr alta cohesión implementando los siguientes principios: abstracción, separación de intereses y ocultamiento de la información.

## 3. Principio de **Diseño para el Cambio**
El software se encuentra en constante cambio y los cambios son, con frecuencia, difíciles de prever. La idea detrás del **diseño para el cambio** es que te anticipes a cambios previsibles en la arquitectura.

Para manejar los cambios esperados podrías, por ejemplo, reunir y considerar con anticipación requerimientos más extensos. Las ambigüedades en la especificación de requerimientos pueden indicar requerimientos funcionales más extensos por venir. Si una funcionalidad no ha sido implementada por razones de costos, considera que esa funcionalidad podría implementarse en las siguientes versiones del sistema.

En cuanto a los cambios no esperados, podrías adoptar una arquitectura altamente flexible. Sin embargo, considera que este tipo de arquitecturas toman más tiempo de diseñas y conducen a un esfuerzo mayor de implementación. Además de que el consumo de recursos puede ser mayor que con arquitecturas inflexibles.

En general, un **diseño para el cambio** se logra consecuentemente aplicando el principio de bajo acoplamiento. Algunos ejemplos son: AOS (Arquitectura Orientada a Servicios) o POA (Programación Orientada a Aspectos).

## 4. Principio de **Separación de Intereses**
**Divide y vencerás**
El principio de **separación de intereses**, en general, establece que deberías separar diferentes aspectos de un problema y lidiar con cada uno de estos sub-problemas individualmente, de esta manera se reduce la complejidad.

El uso más importante de la **separación de intereses** es la **modularización**. Con frecuencia, los requerimientos funcionales son tomados como criterio para la descomposición de un software. Así, cada bloque de construcción cumple con una funcionalidad específica.

Es difícil considerar la separación de los intereses uni-dimensionalmente. Por ejemplo, la descomposición puede ser basada en la funcionalidad pero también se puede separar la función principal de aspectos tales como la gestión de transacciones, seguridad, registro, etc.

## 5. Principio de **Ocultamiento de la Información**
El ocultamiento de la información es un principio fundamental para estructurar y entender sistemas complejos. En general, establece que a un cliente solo se le muestra esa parte de la información que realmente es necesaria para su tarea y la información restante se oculta.

El ocultamiento de la información se aplica en la modularización de un software. Las decisiones de diseño se encapsulan en un bloque de construcción  y se dan a conocer externamente a través de interfaces bien definidas.

Un ejemplo de este principio es el patrón de diseño **Fachada** el cual es un objeto que protege el acceso directo a un subsistema entero. La fachada proporciona una interfaz común de los bloques de consutrcción de un subsistema y esto oculta el subsistema que yace detrás de los bloques de construcción. Un ejemplo de fachada es un intérprete que usualmente consiste de distintos bloques tales como _parsers_, implementación de elementos de lenguaje, compiladores, etc.

### Ocultamiento de la información mediante la creación de capas
Una arquitectura en capas usualmente se estructura de tal forma que cada capa solo vee la capa directamente debajo de ésta. Una capa debe ser accedida solamente mediante interfaces limpias tanto como sea posible. Una capa no debe ver ningún objeto específico o detalles de implementación de ninguna otra capa.

## 6. Principios de **Abstracción**
Abstracción significa enfocarse en aspectos de un concepto que son relevantes para un propósito específico y dejar de lado detalles no importante para este propósito particular. Por lo tanto, la abstracción es un case especial de la **separación de intereses**: se separan los detalles importantes de los menos importantes.

La arquitectura de software contiene algunos sub-principios especiales de abstracción respecto a las abstracciones de interfaces. El resultado de la aplicación de estos principios de abstracción debe ser un _enfoque en las interfaces_: una arquitectura realmente toma efecto a través de las relaciones de los bloques de construcción a otro. Las interfaces del bloque son importantes para estas relaciones que se crean y para su calidad. En detalle, os principios para las abstracciones de interfaz son:

  - Interfaces explícitas
  - Separación de la interfaz y su implementación
  - Principio de sustitución de Liskov
  - Principio de segregación de interfaz
  - Soporte de lenguaje para abstracciones
  - Diseño por contrato

Un ejemplo en el que la abstracción se encuentra muy conectada al ocultamiento de la información es la **portabilidad**. Por ejemplo, las máquinas virtuales que pueden ejecutar un _byte code_ de un lenguaje de programación en múltiples sistemas operativos y capas de acceso a bases de datos que soportan operciones en diferentes productos de bases de datos con una interfaz uniforme.

## 7. Principio de **Modularidad**
La arquitectura de un sistema debe ser constituida de bloques de construcción con responsabilidades funcionales claramente distinguibles. La modularidad se usa para hacer que los bloques de una arquitectura sean modificables, extensibles y reusables.

El principio de modularidad establece que debes esmerarte en obtener bloques de construcción auto-contenidos con relaciones arquitectónicas simples y estables.

Hay varios enfoques que conducen a la modularidad de una arquitectura de software, por ejemplo orientación de objetos, enfoque de componentes, arquitecturas en capas, arquitecturas multiniveles y muchas más. Para implementar el principio de modularidad puedes aplicar los principios de separación de intereses y ocultamiento de la información, además de la abstracción con la que se encuentra fuertemente conectada.

La modularidad conduce al bajo acoplamiento y la alta cohesión ya que te permite encapsular intereses relacionados en un bloque de consutrucción modular.

Un aspecto importante de la modularidad es el principio _abierto/cerrado_, el cual establece que los bloques de construcción deben ser abiertos al cambio pero cerrados para el uso de sus detalles internos por otros bloques de construcción.

## 8. Principio de **Trazabilidad**
Para asegurar que una arquitectura sea comprensible es importante garantizar la trazabilidad de estructuras arquitectónicas y las decisiones. Idealmente, debe existir correspondencia entre un requerimiento del sistema y el bloque de construcción que lo implementa.

Una técnica para mejorar la trazabilidad es indicar -tanto en el código fuente como en los documentos de diseño la estructura arquitectónica a la que se asocia cada uno (p.ej. comentarios). Otra forma puede ser que en el código se incluyan metadatos que hagan referencia a los requerimientos de un bloque de construcción.

La trazabilidad ayuda a obtener bajo acoplamiento y alcanzar un diseño para el cambio porque hace que las estructuras sean más fáciles de comprender y por tanto más independientes y modificables.

## 9. Principio de **Auto-documentación**
La auto-documentación significa que el arquitecto o desarrollador de un bloque de construcción debe tratar de hacer que cada elemento de información de dicho bloque sea parte del bloque de construcción mismo. Esto respalda al **diseño para el cambio** en cuanto a los cambios en la documentación y otra información adicional.

Con frecuencia, se realizan pequeños cambios en el _software_ y no se documentan. Por lo tanto, el código, la documentación, las descripciones arquitectónicas, diseños y otras descripciones de un sistema se vuelven inconsistentes.

La **auto-documentación** se relaciona con la trazabilidad: la información que existe directamente en el blqoue de construcción puede ser fácilmente rastreada. Otro beneficio de este principio es que la documentación se puede usar para generar documentos relacionados que tienen que crearse basado en el código y otra información. Por ejemplo, la documentación en HTML de una API generada automáticamente mediante **JavaDoc**.

## 10. Principio de **Incrementalidad**
**Los intentos por diseñar un sistema entero de una sola vez, con frecuencia fallan** porque, por ejemplo, le diste demasiado valor a aspectos incidentales o porque los aspectos importantes fueron pasados por alto.
Puesto que, con frecuencia, las arquitecturas de _software_ son muy complejas, en un nuevo desarrollo (el primer diseño arquitectónico) tanto como en un sistema existente (los cambios) deben implementarse tan tarde como sea posible.

Estas situaciones surgen, por ejemplo, porque los arquitectos y desarrolladores (entrenados en aspectos técnicos) usualmente no hablan el mismo lenguaje que los expertos en el dominio y porque ambas partes dan por hecho que se han ententido cosas que no son claras para alguien no experto en el campo.

Para evitar este tipo de malentendidos, **desarrolla incrementalmente y obtén retroalimientación frecuente**. Algunas reglas podrían ser:
  - Entrega temprana de primeras versiones de un sistema
  - Opinión temprana de usuarios reales del sistema
  - Introducción de nuevas funcionalidades _paso a paso_

Por lo tanto, la _**incrementalidad**_ significa aplicar el principio de **separación de intereses** a los pasos del desarrollo en el desarrollo del sistema.

### Crecimiento gradual (Piecemeal growth)
La idea es dejar que una arquitectura crezca _paso a paso_. Después de cada paso hay un asesoramiento que conlleva una decisiónn sobre qué hacer enseguida. Esto significa que hay una planeación anticipada muy pequeña o no la hay.

### Prototipado
Muchas veces tiene sentido desarrollar prototipos simples antes de desarrollar un producto a fin de conocer mejor el problema. A veces estos prototipos se convierten en productos; otras veces tiene más sentido tirar el prototipo y empezar de nuevo. Un prototipo le da al arquitecto y al desarrollador un entendimiento de los problemas reales del dominio. Otra forma podría ser un prototipo evolucionario que es un prototipo que se puede desarrollar incrementalmente hasta convertirse en producto.

## Referencias
[Software Architecture](http://www.springer.com/gp/book/9783642197352)
