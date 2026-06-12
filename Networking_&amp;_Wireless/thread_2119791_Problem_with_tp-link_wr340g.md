---
title: "Problem with tp-link wr340g"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by ignaciop on 2013-02-24
Hello i´m new with ubuntu, sorry that my first post is a problem. I past from Windows Vista and start to have problems with connecting facebook and hotmail (not with other pages). I connect to others brand of routers, for example Tenda, and i don´t have this problem. I don´t know what is happening but i supouse the router is blocking me the connection. I erased cookies from the Chromium and Firefox browsers but the problem continues.

I forgot to say that when i connect via wire, direct to the modem, (not to the router) i don´t have the problem

Thanks and sorry for the mistakes.

---

### Post by steeldriver on 2013-02-25
Hello and welcome to the forum

When connected via the router, please post the outputs from these commands in a terminal

```
ifconfig

ping -s 1472 -c 4 -M do facebook.com
```

---

### Post by ignaciop on 2013-02-25
Hello thanks for respond. Here are the results of the comands:

ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1e:68:44:5b:89  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:140 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:140 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:13183 (13.1 KB)  TX bytes:13183 (13.1 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:0d:f0:59:4b:c0  
          Direc. inet:192.168.1.102  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::20d:f0ff:fe59:4bc0/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:615 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:487 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:465066 (465.0 KB)  TX bytes:61545 (61.5 KB)

ping -s 1472 -c 4 -M do facebook.com

PING facebook.com (173.252.110.27) 1472(1500) bytes of data.

--- facebook.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3025ms

---

### Post by steeldriver on 2013-02-25
Sometimes these connectivity issues are due to MTU size - see what happens if you reduce the ping number e.g.

```
ping -s [COLOR=Blue]1428 [/COLOR]-c 4 -M do facebook.com
```

---

### Post by ignaciop on 2013-02-25
I proved this command and the number of packets lost is o% but the problem continues.

The Chromium browser give me this error:

Error 324 (net::ERR_EMPTY_RESPONSE)

---

### Post by steeldriver on 2013-02-26
The ping command doesn't actually change anything - it just tests if MTU / fragmentation is an issue - did you actually edit the wireless connection and change the MTU from 'automatic' to a lower number e.g. 1456 (= 1428 + 28) ?

Regards

---

### Post by ignaciop on 2013-02-26
I went to wireless connection and said automatic.

It´s so wired this problem, i have read a post like my problem, here is:
[http://ubuntuforums.org/showthread.php?t=2014620](http://ubuntuforums.org/showthread.php?t=2014620)

---

### Post by steeldriver on 2013-02-26
you need to change it FROM automatic TO a number like 1456

or you can use ifconfig

```
sudo ifconfig wlan0 mtu 1456
```

but it is better to use the GUI connection editor so that the change will be saved for next time you use the connection

---

### Post by ignaciop on 2013-02-26
Thank youuu veryy much!!!!!!!!!!!!!!!! The problem is resolved.

---

### Post by ignaciop on 2013-04-24
hello again. i have another question. do you know how to resolve the same problem in a tablet with android?

---

