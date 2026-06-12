---
title: "problems connecting to internet through cable modem  (intrepid, 8.10)"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by pat-a-pete on 2009-05-03
Hi, 

I´m using a Laptop with Ubuntu Intrepid (8.10). Normally connecting via ethernet and wireless works fine (at work, in hotels, at home). But.. I´m now on vacation visiting relatives and want to connect here to the internet via a cable modem (Ambit U10C018), .. but I don´t get it to work.

Note: 
the connection to the internet works for a desktop computer with Windows XP and the very same cable modem without problems. 

on the windows machine:
```
ipconfig /all
```gives:
```

Configuración IP de Windows

        Nombre del host . . . . . . . . . : desktop
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo . . . . . . . . . .  : desconocido
        Enrutamiento habilitado. . . . . .: No
        Proxy WINS habilitado. . . . .    : No
        Lista de búsqueda de sufijo DNS:    une.net.co

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS : une.net.co
        Descripción. . . . . . . . . . .  : NIC Fast Ethernet PCI Familia RTL8139 de Realtek #2
        Dirección física. . . . . . . . . : 00-13-8F-A8-23-34
        DHCP habilitado. . . . . . . . .  : No
        Autoconfiguración habilitada. . . : Sí
        Dirección IP. . . . . . . . . . . : 201.233.XX.YYY
        Máscara de subred . . . . . . . . : 255.255.192.0
        Puerta de enlace predeterminada   : 201.233.64.1
        Servidor DHCP . . . . . . . . . . : 10.158.128.2
        Servidores DNS . . . . . . . . . .: 200.13.249.101
                                            200.13.224.254
        Concesión obtenida . . . . . . .  : domingo, 03 de mayo de 2009 20:22:44

        Concesión expira . . . . . . . . .: lunes, 04 de mayo de 2009 1:33:52

```(i replaced the detailed IP-address with "XX.YYY", this is not the "original" output)

When I connect the ethernet-cable coming from the cable modem to my ubuntu laptop, I don´t get an internet connection when selecting "auto eth0" in the gnome-network-manager. 

I´ve tried to set the IP-address, DNS server, gateway and so on from windows in the gnome-network-manager, but with no effect. 

I´ve tried to set the IP-address in the  gnome-network-manager to some "local" one (192.168.10.10). Doing that, I could reach the web-page of the cable modem (192.168.100.1, according to the user manual), but I still did not get a connection to the internet (I played around with setting the DNS servers, gateway, netmask according to the numbers read from windows as well, .. with no effect).

Unfortunately, there is no accessible wireless around and no second network-plug on the desktop to "forward the internet" via the windows computer to my laptop, so downloading packages and so on is not directly possible.


Maybe someone of you has some suggestions of what I could try. 
thanks, 
Peter

---

### Post by pytheas22 on 2009-05-03
Try running these commands:
```

lspci -nn
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:13:8F:A8:23:34
sudo ifconfig eth0 up
sudo dhclient eth0
dmesg | grep -e eth -e rtl
```

Please post all the output (if you can't get Ubuntu online to post the output, save it to a text file and transfer it to a Windows computer for posting here).  These commands should get you online, or if they fail, they should help us figure out what's wrong.

And are you sure the Windows computers at your current location just plug into the cable modem and get connected?  There's no password to enter or other software involved?

---

### Post by pat-a-pete on 2009-05-04
Hi pytheas22, 

Thanks for your reply! That was really quick, I'm impressed to get an answer that fast! 

I ran the commands you posted, and -- wow -- it works. I can get access to the internet with my laptop!

But I'd still like to understand what the cause of the connection problem has been to be able to resolve it by myself if I face the problem another time at another place. 

The output to the commands you posted might give you a clue of what went wrong:

```

peter@jefe:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)



peter@jefe:~$ sudo /etc/init.d/NetworkManager stop
 * Stopping NetworkManager...                                                                                                                           [ OK ] 


peter@jefe:~$ sudo ifconfig eth0 down


peter@jefe:~$ sudo ifconfig eth0 hw ether 00:13:8F:A8:23:34


peter@jefe:~$ sudo ifconfig eth0 up


peter@jefe:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 25710
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:8f:a8:23:34
Sending on   LPF/eth0/00:13:8f:a8:23:34
Sending on   Socket/fallback
DHCPREQUEST of 200.116.245.55 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 200.116.245.55 on eth0 to 255.255.255.255 port 67
DHCPACK of 200.116.245.55 from 10.142.0.1
bound to 200.116.245.55 -- renewal in 12799 seconds.



peter@jefe:~$ dmesg | grep -e eth -e rtl
[    4.530231] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1d:09:5d:80:15
[    4.530235] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    4.530237] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.614733] Driver 'sd' needs updating - please use bus_type methods
[    4.809745] Driver 'sr' needs updating - please use bus_type methods
[   62.214743] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.890208] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   63.890213] tg3: eth0: Flow control is on for TX and on for RX.
[   63.890398] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   74.556138] eth0: no IPv6 routers present
[  301.136081] tg3: eth0: Link is down.
[ 1665.144627] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1665.144632] tg3: eth0: Flow control is on for TX and on for RX.
[ 1735.570436] tg3: eth0: Link is down.
[ 3050.680955] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 3050.680969] tg3: eth0: Flow control is on for TX and on for RX.
[ 3083.237012] tg3: eth0: Link is down.
[18439.603387] tg3: eth0: Link is up at 100 Mbps, full duplex.
[18439.603401] tg3: eth0: Flow control is on for TX and on for RX.
[18524.748019] tg3: eth0: Link is down.
[22816.162929] ADDRCONF(NETDEV_UP): eth0: link is not ready
[22817.840586] tg3: eth0: Link is up at 100 Mbps, full duplex.
[22817.840596] tg3: eth0: Flow control is on for TX and on for RX.
[22817.841591] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[22827.901051] eth0: no IPv6 routers present
[22906.897015] tg3: eth0: Link is down.
[23159.862075] ADDRCONF(NETDEV_UP): eth0: link is not ready
[42445.396457] ADDRCONF(NETDEV_UP): eth0: link is not ready
[42683.330145] ADDRCONF(NETDEV_UP): eth0: link is not ready
[48698.375046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[54360.559060] ADDRCONF(NETDEV_UP): eth0: link is not ready
[65201.406362] ADDRCONF(NETDEV_UP): eth0: link is not ready
[71251.912435] ADDRCONF(NETDEV_UP): eth0: link is not ready
[75069.493948] tg3: eth0: Link is up at 100 Mbps, full duplex.
[75069.493962] tg3: eth0: Flow control is on for TX and on for RX.
[75069.494430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[75080.096018] eth0: no IPv6 routers present
[75128.193018] tg3: eth0: Link is down.
[75196.052979] tg3: eth0: Link is up at 100 Mbps, full duplex.
[75196.052992] tg3: eth0: Flow control is on for TX and on for RX.
[75391.400020] tg3: eth0: Link is down.
[75403.415756] tg3: eth0: Link is up at 100 Mbps, full duplex.
[75403.415769] tg3: eth0: Flow control is on for TX and on for RX.
[75582.204967] tg3: eth0: Link is down.
[75702.697921] tg3: eth0: Link is up at 100 Mbps, full duplex.
[75702.697934] tg3: eth0: Flow control is on for TX and on for RX.
[76015.780066] tg3: eth0: Link is down.
[84896.838647] tg3: eth0: Link is up at 100 Mbps, full duplex.
[84896.838652] tg3: eth0: Flow control is on for TX and on for RX.
[85207.407059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[85209.049303] tg3: eth0: Link is up at 100 Mbps, full duplex.
[85209.049315] tg3: eth0: Flow control is on for TX and on for RX.
[85209.049776] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[85219.388015] eth0: no IPv6 routers present
[85567.037547] ADDRCONF(NETDEV_UP): eth0: link is not ready
[85568.630430] tg3: eth0: Link is up at 100 Mbps, full duplex.
[85568.630441] tg3: eth0: Flow control is on for TX and on for RX.
[85568.632115] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[85612.489301] ADDRCONF(NETDEV_UP): eth0: link is not ready
[85614.067798] tg3: eth0: Link is up at 100 Mbps, full duplex.
[85614.067811] tg3: eth0: Flow control is on for TX and on for RX.
[85614.068264] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


```To answer your question if another password or software (on the windows machine) was involved:
Password: I don't think so, the owner gave me all her documents and I didn't find anything (and since it works after using your commands, I suppose there is none)
software: there is a cable modem install CD, but it seems to be only the manual and a usb driver (and i am connected through ethernet).

thanks a lot for your help, 
Peter

---

### Post by pytheas22 on 2009-05-04
I'm glad it worked.  If you reboot your computer, you will need to run those commands again to connect.

There are two possibilities as to what was wrong.  One is that for some reason, a bug or other problem in NetworkManager was preventing it from connecting you successfully, but it worked from the command line.

The other possibility is that the modem to which you attempted to connect was configured to give IP addresses only to certain computers.  One of the commands you ran ('sudo ifconfig eth0 hw ether 00:13:8F:A8:23:34') temporarily changed your computer's MAC address to match the MAC of the Windows computer that had already connected (its MAC was included in the 'ipconfig /all' output that you posted).  If you want to know for sure if the MAC address was part of the problem, reboot the computer and run just these commands:

```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 up
sudo dhclient eth0
```

If this works, then the MAC address doesn't matter, and there was probably just a bug with NetworkManager.

---

