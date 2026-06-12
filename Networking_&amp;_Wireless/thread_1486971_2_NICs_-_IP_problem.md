---
title: "2 NICs - IP problem"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by JaRiL on 2010-05-18
Hi all,

I've got a server with Ubuntu Desktop 9.10. I use it to run a VMWARE server with several virtual machines.  My first network interface has a 192.168.1.10/24, and works fine.

The problem has come when I've tried to configure my second NIC. I've another PC and they're connected using a 1Gbps link back to back. I'm using 192.168.250.1/30 in the server and the PC has 192.168.250.2/30 with Windows7. When I turn off the PC, the server loses IP and interface goes down, and when I turn it on again, I have to configure IP manually.

This is the config:

[FONT=Courier New]jaril@Mordisquitos:~$ cat -e /etc/network/interfaces
auto lo$
iface lo inet loopback$
$
auto eth2$
iface eth2 inet static$
address 192.168.1.10$
gateway 192.168.1.1$
netmask 255.255.255.0$
network 192.168.1.0$
broadcast 192.168.1.255$
$
auto eth4$
iface eth4 inet static$
address 192.168.250.1$
netmask 255.255.255.252$
network 192.168.250.0$
broadcast 192.168.250.3$
$
$
jaril@Mordisquitos:~$ ifconfig -a

eth2      Link encap:Ethernet  direcciÃ³nHW 00:0e:a6:40:56:ba
          Direc. inet:192.168.1.10  Difus.:192.168.1.255  MÃ¡sc:255.255.255.0
          DirecciÃ³n inet6: fe80::20e:a6ff:fe40:56ba/64 Alcance:Enlace
          ACTIVO DIFUSIÃN FUNCIONANDO MULTICAST  MTU:1500  MÃ©trica:1
          Paquetes RX:3251406 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:52176977 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:1256610455 (1.2 GB)  TX bytes:3060121945 (3.0 GB)
          InterrupciÃ³n:22


eth4      Link encap:Ethernet  direcciÃ³nHW 00:22:f7:20:0e:8c
          Direc. inet:192.168.250.1  Difus.:192.168.250.3  MÃ¡sc:255.255.255.252
          DirecciÃ³n inet6: fe80::222:f7ff:fe20:e8c/64 Alcance:Enlace
          ACTIVO DIFUSIÃN FUNCIONANDO MULTICAST  MTU:1500  MÃ©trica:1
          Paquetes RX:2984463 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5776205 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:192204137 (192.2 MB)  TX bytes:3243846271 (3.2 GB)
          InterrupciÃ³n:20 DirecciÃ³n base: 0x2000

lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  MÃ¡sc:255.0.0.0
          DirecciÃ³n inet6: ::1/128 Alcance:AnfitriÃ³n
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  MÃ©trica:1
          Paquetes RX:65 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:65 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:7003 (7.0 KB)  TX bytes:7003 (7.0 KB)

vmnet1    Link encap:AMPR NET/ROM  direcciÃ³nHW
          Direc. inet:172.16.67.1  MÃ¡sc:255.255.255.0
          ACTIVO FUNCIONANDO  MTU:0  MÃ©trica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:16777580 carrier:54
          colisiones:0 long.colaTX:0
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

jaril@Mordisquitos:~$[/FONT]

The strange caracters are due Spanish keyboard layout.

As you can see, the only difference between both interfaces is the gateway. Eth4 hasn't gateway because is a 2 hosts network.

If I restart network services, I lose eth4 configuration, and I have to config again with ifconfig command.


Anybody has had the same problem?


Many thanks in advance for your help!!
JaRiL

---

