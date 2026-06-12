---
title: "Problem with wired connection"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by aniceto on 2009-11-13
Hi to everybody, i have a problem with my wired connection. I have ubuntu netbook remix on HP 110-1020la and it works fine, the sound out of the box, power management and so on. The wired connection worked well, but today i tried to connect via wire and i couldn't.

First of all when i connected the cable, it appears the icon upside that it was trying to connect, but you can see in the image disconnected.jpg that it doesn't appear, it appears something like the wireless signal but the wireless isn't active.

If you see in enabledNetwork.jpg the network is enabled.

In noEthConnection.jpg you can see that Auto eth0 doesn't appear nor eth1.

About hardwareDriver.jpg i'm using Wireless Broadcomm controller STA.

And in network tools it appears the network device Ethernet interface (eth1) but by default appears Local lo or something like that, as you can see in networkTools.jpg

So i googled about it and tried some things, like configure the conection manually, or view if the device is recognized, when i type ifcongif in the command prompt appears this:

```

eth1      Link encap:Ethernet  direcciónHW 00:23:4d:5d:a0:b5  
          Dirección inet6: fe80::223:4dff:fe5d:a0b5/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:8 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:480 (480.0 B)  TX bytes:480 (480.0 B)

```I read something in this link:

[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html)

it's about ubuntu 8 but i followed the part about the ping to 82.211.81.158 and the results are the next (then i tried with google.com):

```

oscar@oscarnetbook:~$ ping 82.211.81.158
connect: Network is unreachable
oscar@oscarnetbook:~$ ping google.com
ping: unknown host google.com
oscar@oscarnetbook:~$ 

```I'm connected to a router.

---

