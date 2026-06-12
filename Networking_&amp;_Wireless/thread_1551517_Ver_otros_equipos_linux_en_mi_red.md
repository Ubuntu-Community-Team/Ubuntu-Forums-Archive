---
title: "Ver otros equipos linux en mi red"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by terydrums on 2010-08-12
hola soy nuevo en todo lo que es linux ubuntu, la verdad me ha gustado bastante.. quiero saber como ver equipos linux en mi red de trabajo ( pues tengo otra maquina con ubuntu ), ya que al ir a servidores de red, no me aparece ninguno, quiero saber como hacer para ver o entrar a mis otros equipos linux o windows, ya que al intentar acceder a mi red de windows y me dice que no se puede acceder..
si me podrian ayudar. se los agradeceria..
gracias

---

### Post by scrooge_74 on 2010-08-12
Hola,

vamos por partes.

Para accesar de Linux a Linux tienes varias opciones.

Si quieres ver el contenido de carpetas y grabar o leer archivos usas nfs, con eso puedes montar una carpeta o disco de otra máquina que corra Linux en la tuya corriendo linux como si fuera una carpeta mas.

Si lo que quieres es accesar por la red a una PC con linux para cuestiones de mantenimiento usas ssh y estarías entrando por una terminal.

Si lo que quieres es imprimir usas CUPS, hasta las PCs en windows pueden imprimir usando un servidor cups en linux.

Si lo que quieres es ver archivos desde una PC windows o entrar desde linux a las carpetas compartidas en windows tienes que utilizar SAMBA.

Te recomiendo que te leas un poco sobre NFS, SAMBA, SSH y CUPS

Y has todas las preguntas.

Saludos y bienvenido

---

### Post by terydrums on 2010-08-12
> **scrooge_74 said:**
> Hola,

vamos por partes.

Para accesar de Linux a Linux tienes varias opciones.

Si quieres ver el contenido de carpetas y grabar o leer archivos usas nfs, con eso puedes montar una carpeta o disco de otra máquina que corra Linux en la tuya corriendo linux como si fuera una carpeta mas.

Si lo que quieres es accesar por la red a una PC con linux para cuestiones de mantenimiento usas ssh y estarías entrando por una terminal.

Si lo que quieres es imprimir usas CUPS, hasta las PCs en windows pueden imprimir usando un servidor cups en linux.

Si lo que quieres es ver archivos desde una PC windows o entrar desde linux a las carpetas compartidas en windows tienes que utilizar SAMBA.

Te recomiendo que te leas un poco sobre NFS, SAMBA, SSH y CUPS

Y has todas las preguntas.

Saludos y bienvenido

la verdad me interesan las 4 cosas.. con nfs me estoy volviendo loco la verdad.. no se que estoy haciendo mal y todos los tutoriales que encuentro me dicen lo mismo.
no se por que no puedo compartir.. una pregunta en sierto momento en la instalacion del nfs tengo que reiniciar los procesos cada vez que los pongo me aparece comando erroneo y cuando hago restart del portmap me dice que no se puede.. te doy un ejemplo de lo que quise hacer..
[http://www.youtube.com/watch?v=ZwiP64DQpYs](http://www.youtube.com/watch?v=ZwiP64DQpYs)

asi que si me ayudan.. estaria genial

---

