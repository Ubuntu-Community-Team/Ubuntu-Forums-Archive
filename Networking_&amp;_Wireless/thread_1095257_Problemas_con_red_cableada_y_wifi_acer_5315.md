---
title: "Problemas con red cableada y wifi acer 5315"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by dmela2012 on 2009-03-13
tengo una acer 5315, instale ubuntu, la ultima version, la que me baje ayer. y no me funciona internet, ni cableada ni inalambrica, cableada detecta el cable, trata de conectarse, pero no puede y queda sin conexión. muchas gracias.

---

### Post by luks911 on 2009-03-13
Uff... me costó encontrar el post porque generalmente leo sólo la sección de la comunidad argentina.
A ver, te recomiendo que postees un thread nuevo (no me mates) en la parte del LoCo (Local Community) de Argentina, acá ([http://ubuntuforums.org/forumdisplay.php?f=189](http://ubuntuforums.org/forumdisplay.php?f=189)) en Hardware o en la sección general, para seguirla ahí. Así te va a ayudar más gente, porque en "esta parte" del foro es más común que se postee en inglés y que lea gente que no sabe español, mientras que allá somos todos argentinos :-)

Entre tanto, si la placa wifi es la que decias en el mensaje privado, instalarla es muy fácil si usás intrepid. En una terminal (Aplicaciones > Accesorios > Terminal) ejecutá
```
sudo aptitude install linux-backports-modules-intrepid
```
Te va a pedir tu contraseña y va a instalar una serie de drivers. Luego vas a Sistema > Administración > Controladores de Hardware, y deshabilitás los drivers de wifi que estén habilitados y habilitás el que tiene el nombre "Support for 5xxx series of Atheros 802.1 wireless LAN cards". Reiniciás y el wifi va a funcionar.

Con respecto a la conexión a Internet, seguro vas a encontrar más ayuda postenado en la sección argentina. ¿El proveedor es fibertel? Porque leí varios casos similares al tuyo con fibertel y creo que tiene que ver no con Ubuntu sino con el cambio de máquina o algo por el estilo. Pero da bien los detalles en el nuevo post que varios te van a responder.

Un saludo

---

### Post by dmela2012 on 2009-03-14
Muchas gracias, ahora lo voy a poner en la parte de argentina. Me funcionó bien lo que me dijiste, muchas gracias, tuve wifi, pero despues actualice todo, y cuando reinicié, ahora no tengo más, me muestra el atheros, con el driver, y me dice que esta habilitado pero que no lo estoy usando.

---

### Post by luks911 on 2009-03-14
Ejecutá en una terminal
```
sudo lshw -C Network
```
y pegá el resultado acá. Eso va a mostrar, entre otras cosas, cuál es el driver que está tratando de usar.

PD: Si querés hacelo en el nuevo thread.

---

