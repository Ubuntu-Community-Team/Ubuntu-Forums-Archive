---
title: "no internet connection ubuntu 11.04"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by chankins on 2011-07-01
please help,

running ubuntu 11.04

i can't get my internet connection working, here's what happened:

computer wouldn't boot-up, replaced the power-supply and bought a new case.
put everything in the new case, works fine, but no internet, it always worked before.

i'm not using a router, directly connected to modem.

ifconfig shows hwaddr 00:00:00:00:00:00, so i called cable company got mac address for modem, cable company
tells me everything is working fine from their end, my system isn't 'talking' to the modem.



edited /etc/network/interfaces so it shows:

```
auto lo
iface lo inet loopback

#added these 3 lines
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:1e:46:7f:4d:7e
```



now the pc/activity light on the modem blinks, and everything looks ok but still no internet.
ifconfig shows:

```
chris@chris-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:46:7f:4d:7e  
          inet6 addr: fe80::21e:46ff:fe7f:4d7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:568395 (568.3 KB)  TX bytes:27961 (27.9 KB)
          Interrupt:16 
```



no ip address, i think maybe dhcp isn't giving me one: so:

```
chris@chris-desktop:~$ sudo dhclient -v
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

No broadcast interfaces found - exiting.
```



No idea where to go from here....

also this is my ethernet card:

```
chris@chris-desktop:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:1e:46:7f:4d:7e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fdcfc000-fdcfffff ioport:ac00(size=256) memory:fdb00000-fdb1ffff

```


please help...

Chris.

---

### Post by chili555 on 2011-07-01
Is Network Manager running on the computer?```
ps aux | grep -i network
```If it is, it will probably interfer with manual methods making it very difficult to connect.> chris@chris-desktop:~$ sudo dhclient [COLOR="Red"]-v[/COLOR]All this does is print out the version. What does this tell us?```
sudo dhclient eth0
```

---

