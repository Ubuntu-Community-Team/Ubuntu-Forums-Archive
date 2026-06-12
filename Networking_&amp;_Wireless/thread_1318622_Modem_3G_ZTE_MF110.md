---
title: "Modem 3G ZTE MF110"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by thejavo on 2009-11-07
Finalmente consegui que esto funcionara. Baje el paquete de usb_modeswitch 1.05 de
[http://packages.ubuntu.com/lucid/usb-modeswitch]("http://packages.ubuntu.com/lucid/usb-modeswitch"), lo baje de ahi porque la version de karmic es la 1.02, en los paquetes esta la de Lucid que es la 1.05, actualmente el proyecto va por la 1.07, como la 1.05 anduvo, deje esa.

despues de eso van a /etc/usb_modeswitch.conf y agreguen al final del archivo lo siguiente:

[I]########################################################
# ZTE MF110
#
# by thejavo
########################################################

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x1
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

#Si el ultimo no anduvo prueben estos otros dos.
;MessageContent="5553424312345678000000000000061b000000030000000000000000000000"
;MessageContent="55534243003cae880000000000000600000000000000000000000000000000"
[/I]

y eso es todo, reinicien y lo tiene que detectar solito, si no quieren reiniciar prueben de poner:

sudo usb_modeswitch

antes de correrlo si quieren pongan lsusb, ahi van a encontrar un dispositivo que dice 19d2:2000 
despues de correr el usb_modeswitch, si todo anduvo bien, deberían ver con lsusb el dispositivo como: 19d2:0031

Si el messageContent no es el de su modem, puede realizar el cambio pero seguir sin funcionar, espero les sirva.

---

### Post by marcosnc on 2009-11-19
Hola thejavo, yo también estoy teniendo problemas para hacer andar el modem ZTE MF100 en ubuntu. Tengo instalado el 8.10 todavía. Seguí unos cuantos howto's para hacerlo andar y todavía no pude. Todos apuntan a cambiar el modo del "aparatito" usando el usb_modeswitch y creo que el problema que estoy teniendo está ahí.
Supuestamente luego de ejecutar esa aplicación, el comand lsusb debría listar el modem como "ID 19d2:0031" pero a mi siempre me aparece "ID 19d2:2003" no tengo ni idea por qué...
Avisame si seguís con el problema o si ya lo solucionaste.
Saludos,
Marcos.

---

### Post by danpos on 2009-11-21
@All

Hi guys! One brazilian member from ubuntuforum-br.org posted that (he just upgraded to Ubuntu 9.10) that using this version of usb-modemswitch ([usb-modeswitch_0.9.7_i386.deb](https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb)) did the trick for him (supposing that your installation be 32 bits); also I would suggest to install this other package ([ozerocdoff_0.4-2_i386.deb](https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb)).

Here in my Ubuntu 9.04 these packages did the trick (I'm posting using the 3G - HSDPA - connection from my ZTE MF100 modem ;) ).

Let me know if this tip worked for you.

Lucky,

Danpos.

---

### Post by thejavo on 2009-11-24
Hola, en la version 9.04, seguí varios foros con el tema del usb-modeswitch y logré que pase de 19d2:2000 a 19d2:0031, pero de cualquier forma siguió sin funcionar, como ya estaba por salir el 9.10 y, en teoría se abocaban a resolver esto esperé. Tengo un modem Huawei de claro que funcionó al toque, pero este ZTE MF110 de Personal no he podido. Si lo logro avisaré. Gracias.

---

