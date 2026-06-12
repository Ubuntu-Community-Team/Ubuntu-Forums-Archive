---
title: "Problems with Internet at Ubuntu + VMWare"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Draco351 on 2011-09-17
I have **VMWare Player** and a virtual machine with **Ubuntu 11.04 server**. Since a few days, there are problems connecting to Internet but I'm sure that is not related with my connection because Windows 7 have Internet; same with VMWare Player (I can update it).

I had created [another thread]("http://ubuntuforums.org/showthread.php?t=1844774"), but then a user advised me that the better would be open a new, and explain that I'm using a Virtual Machine (so, is not a normal installation).

Then, I let here information that could be useful:

**$ lspci -nn**
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

**$ lshw -C network**
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

**$ ifconfig -a**
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

**$ route -n**
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic MÃ©tric Ref    Uso Interfaz
```

**$ nslookup ubuntu.com**
```
;; connection timed out; no servers could be reached
```

**$ dig ubuntu.com**
```
; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

[IMG]http://i281.photobucket.com/albums/kk205/LEANDRO351/e787aeba.jpg[/IMG]

[IMG]http://i281.photobucket.com/albums/kk205/LEANDRO351/16db49ee.jpg[/IMG]

Thanks in advance ;-)

---

### Post by Draco351 on 2011-09-18
Up :(

---

### Post by Draco351 on 2011-09-19
UP x2 :(

---

