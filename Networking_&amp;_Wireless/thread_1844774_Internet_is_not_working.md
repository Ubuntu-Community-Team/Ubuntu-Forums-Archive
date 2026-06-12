---
title: "Internet is not working"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by Draco351 on 2011-09-15
I have a problem since four days with Ubuntu and the Internet connection. I have searched a lot of information about the problem, and I have done things like this:

[http://www.taringa.net/posts/linux/1797988/Problema-internet-ubuntu-8_10-___-Solucion.html](http://www.taringa.net/posts/linux/1797988/Problema-internet-ubuntu-8_10-___-Solucion.html)

With these changes, Internet worked correctly **until I installed all pending updates**...  Now I don't know what more can I do.

**Ubuntu 11.04** is installed in a virtual machine using **VMWare Player**, but this is not the problem because VMWare have connection; same with Windows 7.

I have seen in other thread that probably you will need some information like this:

**lspci -nn**
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 01)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 08)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112]
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]
00:10.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
```

**sudo lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 01
       serial: 00:0c:29:c4:54:0e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:17 memory:e8820000-e883ffff memory:e8800000-e880ffff ioport:1080(size=64) memory:80000000-8000ffff
```

**ifconfig -a**
```
eth0      Link encap:Ethernet  direcciónHW 00:0c:29:c4:54:0e  
          Dirección inet6: fe80::20c:29ff:fec4:540e/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:24 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:16 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:2208 (2.2 KB)  TX bytes:3985 (3.9 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  MÃ¡sc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  MÃ©trica:1
          Paquetes RX:53 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:53 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:2765 (2.7 KB)  TX bytes:2765 (2.7 KB)
```

**route -n**
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic MÃ©tric Ref    Uso Interfaz
```

**nslookup ubuntu.com**
```
;; connection timed out; no servers could be reached
```

**dig ubuntu.com**
```
; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

Thanks in advance and if you need more information, just ask.

---

### Post by papibe on 2011-09-15
I see the exact problem than this [thread]("http://ubuntuforums.org/showthread.php?t=1844307"). Could you follow the instructions of my last post and report back?

Regards.

---

### Post by Draco351 on 2011-09-15
With **gksudo /etc/resolv.conf**, and then my password, nothing happened.

I have opened this file with **sudo gedit /etc/resolv.conf** and inside there was the next lines:

```
nameserver 192.168.2.1
nameserver 192.168.2.3
```

Anyway I have deleted it and replaced by:

```
8.8.8.8
8.8.4.4
```

But I get the **same result** with the last 2 commands.

If you need it, this is my **/etc/network/interfaces** (I changed it trying to solve the problem)

```
    auto eth0
    iface eth0 inet static
    adress 192.168.2.3
    netmask 255.255.255.0
    gateway 192.168.2.1
```

And, in relation with your questions at that thread...

[SIZE="3"]**Are you using the desktop version or the server version?**[/SIZE]
Ubuntu 11.04 server \n \l

[SIZE="3"]**Have you uninstall the network manager? (If you are using every thing as was installed the you are using it)**[/SIZE]
Maybe, I'm not sure. I have used these commands:

```
sudo apt-get remove --purge network-manager
sudo gedit /etc/resolv.conf 
sudo gedit /etc/network/interfaces
sudo /etc/init.d/networking restart 
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras (it doesn't work because I don't have internet)
```

---

### Post by papibe on 2011-09-15
:-( my mistake, the correct syntax is:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

### Post by Draco351 on 2011-09-15
Same result with last 2 commands :(

---

### Post by papibe on 2011-09-15
After a second look you are also missing your default route.Try running this:
```
$ sudo route add default gw 192.168.1.1 eth0
```
Then check if the route is sticking:
```
$ route -n
```
It should be a line like this:
```
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```
If it's there, try accessing the Internet using Firefox (it may be necessary restart Firefox).

Tell us how it goes,
Regards.

---

### Post by Draco351 on 2011-09-15
```
$ sudo route add default gw 192.168.1.1 eth0
```

I get:

**SIOCADDRT: El proceso no existe (The process does not exist)**

And with...

```
$ route -n
```

Obviously, is empty :frown:

---

### Post by papibe on 2011-09-15
Try the same command but with this address instead:  192.168.2.1

---

### Post by Draco351 on 2011-09-16
Don't work, I get same error:

**SIOCADDRT: El proceso no existe (The process does not exist)**

---

### Post by Draco351 on 2011-09-16
Could be a problem related with the configuration of Internet devices?

[IMG]http://i281.photobucket.com/albums/kk205/LEANDRO351/e787aeba.jpg[/IMG]

[IMG]http://i281.photobucket.com/albums/kk205/LEANDRO351/16db49ee.jpg[/IMG]

Before, there were 3 devices here and now there are only 2.

---

### Post by papibe on 2011-09-16
I apologize but I didn't realize until now that this was a virtual VMWare machine. I think the best is to create a new thread because this one has going in another direction (my tips where all for a regular install).

Again, sorry.

In Spanish: 
> Amigo, creo que sin querer te he dado mal información. Me acabo de dar cuenta que las instrucciones que te he dado son para una instalación normal y no para una maquina virtual VMWare (yo solo conozco VirtualBox y no hay mucha diferencia con una normal).

Creo que lo mejor es que crees un thread nuevo, incluyendo el el título que es un problema de red con una máquina virtual de VMWare.

Mil disculpas,
Saludos.

---

### Post by Draco351 on 2011-09-17
Don't worry, here is the new thread:

[http://ubuntuforums.org/showthread.php?p=11259236#post11259236](http://ubuntuforums.org/showthread.php?p=11259236#post11259236)

Thanks for all what you are doing ;)

PD: I understand the english without problems, but sometimes is difficult to me write what I want to say. Write only in english if you want, don't have to double work ^^

---

