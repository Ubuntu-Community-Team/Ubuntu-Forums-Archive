---
title: "Wifi doesn't work in ubuntu 9.04"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by andrewbond007 on 2009-05-12
Hola. Tuve serios dolores de cabeza con el tema del wifi en Ubuntu 9.04 y quiero dejar testimonio de ello.
Hi! I had serious headache with wifi in Ubuntu 9.04 and I want to leave a testimony of that.

The article is write in Spanish, I have no time for a complete translation, if anyone have a doubt or doesn't understand any part of this please write below this post or send me a mail to "rodobastias@gmail.com".

Primero que todo les cuento que mi notebook es un HP Pavilion dv5 y que la tarjeta de WIFI es de Atheros Communications Inc, modelo: AR242x 802.11abg Wireless PCI Express Adapter
Resulta que cometí el error de actualizarme a esta nueva versión. Yo estaba muy feliz con Ubunto 8.10 Intrepid Ibex y un día cualquiera entro al gestor de actualizaciones quien me ofrece el "upgrade to new version Ubuntu 9.04". Lamentablemente acepté sin revisar previamente en Internet los problemas de esta versión. El más grave y único que puedo reportar es que NO HAY MODO DE HACER FUNCIONAR EL HARDWARE DE WIFI.
Busqué y busqué soluciones hasta que encontré una que funciono en primera instancia. Fue la siguiente: en otro de miles de foros una persona dejó claro que si habíamos instalado el "support for atheros 5xxx series wireless..." en el kernel 2.6.27-11 este no funcionaría en un nuevo kernel al menos que se actualizara. Esto explicaba claramente lo que sucedía con mi notebook pues la versión 9.04 instala el kernel 2.6.28, así que no funcionaría tal soporte para wifi. Lo que hice entonces fue entrar a la versión 9.04 con el kernel .27 que aparecía en el menú de booteo (grub). Verifiqué que allí podía utilizar sin problemas el "support for atheros 5xxx..." debido y fuí muy feliz.
Todo parecía bien luego de 2 o 3 días de uso PERO, PERO de repente entro a Ubuntu como siempre, hago el paso para habilitar el "support for..." y no funciona, no pasa nada!!!
Busco y busco soluciones nuevamente en la web y no encuentro, no hay soporte para wifi en Ubuntu 9.04. Por esto decido, con pesar y mucha rabia, volver a instalar Ubuntu 8.10, pero acá tampoco acaba de inmediato mi tragedia...

Yo había logrado hacer funcionar mi wifi en Ubuntu 8.10 del siguiente modo: Instalar mediante la consola el paquete "linux-backports-modules-intrepid" (sudo apt-get install linux-backports-modules-intrepid) y luego entré a "System-> Hardware Drivers", allí desactivé el driver que estaba por defecto para wifi (que no funcionaba) y elegí (activé) el famoso "support for atheros 5xxx...". Lo que yo esperaba hacer era lo mismo esta vez con mi recién formateado notebook.
Una vez que se instaló todo el sistema me avisó que habían actualizaciones disponibles (301!!!), entré al update manager, no seleccioné los paquetes para tarjetas NVIDIA ni INTEL porque mi notebook tiene una ATI RADEON y le dí aceptar a la descarga e instalación de todas las novedades.
Me llevé una gran sorpresa cuando instalé el "linux-backports-modules-intrepid" pues luego de revisar los "Hardware Drivers" noté que ya aparecía como habilitado el "Support fot Atheros 5xxx...", pero la wifi NO FUNCIONABA, oh!!! dolor de cabeza!!
Revisé y revisé que podría suceder, desinstalé y volví a instalar "linux-backports..." y nada :(
Resignado volví a instalar el sistema completo Ubunto Intrepid...y pasó la misma historia.
Por un momento me sentí defraudado de Ubuntu y también de Linux cuando descubrí que Fedora y otras distribuciones también tienen serios problemas con la wifi.

Y bueno, muy tarde ya decidí volver a instalar Irepid Ibex nuevamente...
Esta vez tuve mucho cuidado al momento de decidir los paquetes a actualizar, no seleccioné los drivers de NVIDIA, INTEL, actualizaciones para el kernel 2.6.27-7 (pues usaría el 11). Una vez que se instaló todo eso por medio del Terminal instalé a "linux-backports...", reinicié....y AHORA SÍ QUE FUNCIONABA EL WIFI!!!!! :D, tal como antes, sólo que tiene una diferencia que es positiva: no es necesario que uno entre a "Hardware Drivers" cada vez y habilite el driver, sino que comienza a funcionar por sí solo, sólo pide una clave (que debes crear) para autorizar la acción, ¡y ya está!!!

Toda esta historia tiene una gran moraleja: UN NOTEBOOK (O LAPTOP) SIN WIFI NO TIENE GRACIA, POR ELLO CUIDA A TU WIFI CON MUCHO CUIDADO Y ¡NO TE CAMBIES DE KERNEL O DE VERSIÓN DE UBUNTU SIN ANTES AVERIGUAR DETALLES Y POSIBLES PROBLEMAS!!

Les reitero que el "support for Atheros 5xxx series..." funciona perfecto en el kernel 2.6.27-11, con el resto hay problemas.

Esta historia tiene muchos detalles y con ellos he adquirido una pequeña experiencia en esto, por ello si tienes dudas o problemas similares escribe bajo este post o envíame un mail a "rodobastias@gmail.com"

Enjoy Ubuntu and take care of your wifi driver!! :P

---

### Post by andrewbond007 on 2009-05-12
Hi!
At least I want to leave the main message of my post in English: A laptop without wifi doesn't have sense, because of that TAKE CARE OF YOUR WIFI DRIVER AND **DON'T CHANGE THE KERNEL VERSION OR THE UBUNTU (LINUX) DISTRIBUTION WITHOUT FIND OUT ANY DETAILS OR POSSIBLES PROBLEMS.**
THE DRIVER FOR MY ATHEROS CARD IS CALLED **"Support for 5xxx series of Atheros 802.11 wireless LAN cards" AND ONLY WORKS WITH THE KERNEL VERSION 2.6.27-11 GENERIC**, WITH THIS CONFIGURATION YOU CAN BE THE HAPPIEST PERSON IN THE WORLD :D, WITH ANY CHANGE IT POSSIBLY DON'T WORK.

I hope this post can help or serve to the Ubuntu-Linux community.

Best Regards!

Rodrigo.

---

