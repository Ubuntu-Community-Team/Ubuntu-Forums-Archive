---
title: "No internet connection in custom Ubuntu"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by jsevi83 on 2012-10-24
I'm using ubuntu-mini-remix and ubuntu-customization-kit to make a custom ubuntu with less packages than the official 12.10. When testing it from a live usb, everything seems to be working okay, but I have no internet connection.

I can connect to my wireless network with Network Manager, no problem about that, but even if I'm connected there is no traffic at all, as if I wasn't connected to any network. The same happens with ethernet cable. I don't know if I'm missing some package, but with the same ones it used to work in Ubuntu 12.04.

I tried with firefox, gnome terminal and synaptic, all behave as if I wasn't connected to any network, but nm-applet says that I am...  I checked iwconfig and dmesg, and cannot find any reason why it shouldn't be working. Maybe something about permissions? Or missing packages? Any suggestion would be appreciated...

---

### Post by Cheesehead on 2012-10-24
Open a terminal, and paste the result of the command 'ifconfig' here.

---

### Post by jsevi83 on 2012-10-24
It's in Spanish, but easy to understand. I just edited my mac addresses. 
Everything looks exactly the same as in Precise (my current install) except from the third line in **lo** "Dirección inet6: ::1/128 Alcance:Anfitrión", which i dont have in Precise.


eth0      Link encap:Ethernet  direcciónHW zz:zz:zz:zz:zz:zz
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:47 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:232 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:232 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:17480 (17.4 KB)  TX bytes:17480 (17.4 KB)

wlan0     Link encap:Ethernet  direcciónHW zz:zz:zz:zz:zz:zz
          Direc. inet:192.168.1.11  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::1e4b:d6ff:fe5b:ba48/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:11 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1048 (1.0 KB)  TX bytes:1962 (1.9 KB)

---

