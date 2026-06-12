---
title: "Rutear subredes"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by rollyar on 2010-12-28
Hola gente:

Tengo un par de preguntas:

Tengo dos subredes A(192.168.1.0/24) y B(192.168.2.0/24).

Hace unos días instalaron de telecom un VPN, con unos modems a los cuale le pusieron una ip de la red interna esto es el que esta en la red A le pusieron 192.168.1.10, y el que esta en la red B 192.168.2.10.  
En el servidor de la red A(192.168.1.1) genere una ruta estatica 192.168.2.0/24 -> 192.168.1.10. Y en de la red B otra que redirija lo que va a la red192.168.1.0/24 ->192.168.2.10.
Si hago un ping entre los servidores todo ok, si hago un ping a una maquina especifica todo ok, pero el resto de la red no recibo respuesta.

Las preguntas son es correcto que a estos modems me hayan puesto una ip de mi lan?

Porque de una de las maquinas internas si recibo respuesta del ping y de las otras no, podra ser problema de firewall? 

De momento es eso muchas gracias.

PD: Adjunto una imagen con la red que tengo si de algo sirve, la vpn que esta dibujada va a ser reemplazada por la conexion entre los  modems nombreados como (BRANCH A o B)

---

