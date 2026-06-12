---
title: "Placa WiFi Intel 3945ABG instalada pero en Ubuntu 10.10"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by carlos321 on 2011-04-24
Buen día señores. Tal como lo dice el titulo tuve problemas con la WIFI de mi laptop. Es una HP Pavilion 2220la con la placa WIFI Intel 3945.

Instale Ubuntu 10.10 32bit ( El pc es dual core pero 32bits )
No podía hacer que el led del switch encienda en azul, lo que menos me importa es el color de la lamparita, pero cuando el led prende azul es por que la placa esta ON.

Instale linux mil veces desde hace 10 años fácilmente, pero siempre por un motivo u otro no pude hacer que sea mi sistema operativo 100%.

Hice detodo un poco para solucionar el tema de la WIFI, leí mil post y en resumidas cuentas el probema era el siguiente.

La placa estaba bien intalada.
El sistema la veia pero no me la mostraba. Cuando puse otra placa WIFI USB me mostro las dos en el listadode "Miniaplicación Gestor de la red "
Las dos estaban apagadas-

Resulta que este PC no tiene Bluethoot. Pero se instalan y corren "cositas" por default (No se si es driver o aplicación) y esto genera "confusión informática"

Lo solucione con lo siguiente:

Con esto apague el bluethoot:

**sudo rfkill block bluetooth**

Y con esto prendí la WIFI

**sudo rfkill unblock wifi**


No se que pasara cuando conecte un dispositivo bluethoot, pero ya lo veremos mas adelante.


Es mi primer post y mis primeras horas comprometido con con que Linux sea mi sistema operativo 100%, sepan disculpar.

Gracias a la comunidad.

---

### Post by josephmills on 2011-04-24
this is what it looks like in english 



Intel 3945ABG WiFi motherboard installed but Ubuntu 10.10
Good morning gentlemen. As the title says I had problems with the WIFI on my laptop. HP Pavilion 2220la is a plate with Intel WIFI 3945.

Install 32bit Ubuntu 10.10 (The pc is dual core but 32bits)
I could not make the switch LED lights up in blue, the least I care about is the color of the bulb, but when the LED turns blue is because the plate is ON.

Install linux thousand times over 10 years easily, but always for one reason or another could not make it my operating system 100%.

Detodo did a little to address the issue of WIFI, I read a thousand post and to sum up the probem was next.

The plate was well Intal.
The system but I saw showed it. When I put another plate USB WIFI showed me both in listadode "Network Manager Applet"
The two were off-

It turns out that this PC does not have Bluethoot. But are installed and run "stuff" by default (if not driver or application) and this creates "confusion computing"

Solve it with the following:

With this turn the Bluethoot:

sudo rfkill block bluetooth

And with that I turned on the WIFI

sudo rfkill unblock wifi


Do not know what will happen when you connect a device Bluethoot, but we'll see later.


This is my first post and my first few hours committed to Linux as my operating system 100%, are able to forgive.

Thanks to the community.

---

### Post by Elfy on 2011-04-24
Hi - this is an english forum. Please look here - [http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183) for a Loco forum more suited to your issue.

Further options here - [http://www.ubuntu.com/support/community/locallanguage#spanish](http://www.ubuntu.com/support/community/locallanguage#spanish)

> Write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.


Thread closed.

@carlos321 - if you want this moved to a Loco forum please PM me and I will move it there for you.

---

