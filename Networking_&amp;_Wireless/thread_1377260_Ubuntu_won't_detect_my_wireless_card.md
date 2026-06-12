---
title: "Ubuntu won't detect my wireless card"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by alvin4 on 2010-01-10
Just like the title said it won't detect my wireless card. Anybody know what's wrong with it?

---

### Post by lindsay7 on 2010-01-10
You need to provide the details of your card and or computer.

---

### Post by alvin4 on 2010-01-10
> **lindsay7 said:**
> You need to provide the details of your card and or computer.What details do you need? I will be glad to provide them.

---

### Post by lindsay7 on 2010-01-10
Make, models, part numbers, etc., etc.  You can not get much help with out some detail.  There are thousands of wireless cards and adaptors and computers and motherboards.

---

### Post by The Toxic Mite on 2010-01-10
Hey!
 
Can you go to Applications --> Accessories --> Terminal, and enter the following commands please?
 
```

sudo lshw -c network
lspci -v less
iwconfig
dmesg

```
 
Post the outputs when done :)
 
-TTM-
 
EDIT:-
 
> **lindsay7 said:**
> Make, models, part numbers, etc., etc. You can not get much help with out some detail. There are thousands of wireless cards and adaptors and computers and motherboards.
 
The only way the OP can find that is if he types in the above terminal commands.

---

### Post by alvin4 on 2010-01-10
> *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:41:a0:5f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)

There you go. Thanks for all the help so far.:D

---

### Post by The Toxic Mite on 2010-01-10
> ```

product: BCM4312 802.11b/g
vendor: Broadcom Corporation

```
 
Urgh, the dreaded B43 driver will be needed ;/
 
Are you able to get a wired connection? If so:
 
```

sudo apt-get install b43-fwcutter

```
 
-TTM- :)

---

### Post by alvin4 on 2010-01-10
> **The Toxic Mite said:**
> Urgh, the dreaded B43 driver will be needed ;/
 
Are you able to get a wired connection? If so:
 
```

sudo apt-get install b43-fwcutter

```-TTM- :)I am currently not able to use my wired connection (I will be able to tomorrow). I am posting on my windows side of my laptop (which can use the wireless card), is there any way I can download what I need in windows and transfer it to ubuntu?

---

### Post by The Toxic Mite on 2010-01-10
> **alvin4 said:**
> I am currently not able to use my wired connection (I will be able to tomorrow). I am posting on my windows side of my laptop (which can use the wireless card), is there any way I can download what I need in windows and transfer it to ubuntu?
 
I wouldn't recommend that because you need an Internet connection to get the firmware for your card. :-k

---

### Post by alvin4 on 2010-01-10
> **The Toxic Mite said:**
> I wouldn't recommend that because you need an Internet connection to get the firmware for your card. :-kI guess I will have to wait until tomorrow.:( I will post how it goes tomorrow.:D

---

### Post by The Toxic Mite on 2010-01-10
> **alvin4 said:**
> I guess I will have to wait until tomorrow.:( I will post how it goes tomorrow.:D
 
Good idea :D
 
-TTM-
 
EDIT: Just subscribed to this thread :)

---

### Post by alvin4 on 2010-01-10
> **The Toxic Mite said:**
> Good idea :D
 
-TTM-
 
EDIT: Just subscribed to this thread :)Thanks for waiting.:D I now have accses to the wired connection. Here is what I get:


> alvin@ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for randy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After this operation, 115kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)'
in the drive '/cdrom/' and press enter


---

### Post by Atzu on 2010-01-10
I believe u need to go to Adminstration -> Software sources and uncheck the thing that says something like Karmic Koala cd 

just uncheck that :p and try again i believe that should do it

---

### Post by alvin4 on 2010-01-10
> **Atzu said:**
> I believe u need to go to Adminstration -> Software sources and uncheck the thing that says something like Karmic Koala cd 

just uncheck that :p and try again i believe that should do itThanks for the reply!:D


I unchecked it, and this is what I get now:

> alvin@ubuntu:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
alvin@ubuntu:~$ 



---

### Post by Atzu on 2010-01-10
Try searching for it in synaptic package manager I believe is also in administration... im not on ubuntu so i dont remember >.>

---

### Post by alvin4 on 2010-01-10
> **Atzu said:**
> Try searching for it in synaptic package manager I believe is also in administration... im not on ubuntu so i dont remember >.>Will this work?:

[http://packages.ubuntu.com/hardy/b43-fwcutter](http://packages.ubuntu.com/hardy/b43-fwcutter)


It's for hardy though.

---

### Post by kyuubi777 on 2010-01-10
I've used packages meant for 8.10 in 9.10, so try it out.. can hurt
if it doesn't work just remove the package later

---

### Post by The Toxic Mite on 2010-01-10
> **Atzu said:**
> I believe u need to go to Adminstration -> Software sources and uncheck the thing that says something like Karmic Koala cd 

just uncheck that :p and try again i believe that should do it

OR he could've just used the god-damn CD :|

---

### Post by alvin4 on 2010-01-10
Hi you guys, I installed the driver, and now when I click on the connections thingy on the toolbar the place where you could click "enable wireless" is grayed out. Anybody know why?



Also, if I uninstalled 9.10, would 8.10 be a good alternative?

---

### Post by alvin4 on 2010-01-11
Hay you guys I got it working. 


This is what I did:

1) I uninstalled ubuntu 9.10

2) I installed ubuntu 9.04

3) It works


But thanks for your help guys :)

---

### Post by The Toxic Mite on 2010-01-12
> **alvin4 said:**
> Hay you guys I got it working. 


This is what I did:

1) I uninstalled ubuntu 9.10

2) I installed ubuntu 9.04

3) It works


But thanks for your help guys :)

Yay! Well done on managing to get your Wi-Fi working! :D

-TTM-

---

### Post by llueveYescampa on 2010-02-16
I am having a similar problem with my wireless card.

Here is the relevant part of output of the 'sudo lshw -c network command:

  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:0a:f8:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:da100000-da101fff


Thank you all in advance for the help provided.

---

### Post by mrpenguin on 2010-02-16
Having the same problem on a friends desktop ...

> matt@matt-2:~$
matt@matt-2:~$ sudo lshw -c network
[sudo] password for matt:
*-network:0
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: b
bus info: pci@0000:02:0b.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32
resources: irq:9 memory:dc800000-dc801fff
*-network:1
description: Ethernet interface
product: RTL-8029(AS)
vendor: Realtek Semiconductor Co., Ltd.
physical id: d
bus info: pci@0000:02:0d.0
logical name: eth0
version: 00
serial: 00:80:c8:f3:7e:b4
width: 32 bits
clock: 33MHz
capabilities: ethernet physical
configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.1.108 latency=0 multicast=yes
resources: irq:11 ioport:d400(size=32)
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:19:7d:24:de:be
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
matt@matt-2:~$ 

---

