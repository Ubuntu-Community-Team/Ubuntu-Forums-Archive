---
title: "Installing Wireless card WNA 1000 . netgear wireless N 150 card."
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by odogwu on 2010-03-18
dear Ubuntu daddies,

i need serious help guys. i'm trying to install WNA 1000 wireless card on my system and Ubuntu is not reading the card. I have tried installing bcmlw or something as suggested in another post to no avail. I have also tried downloading compat wireless and changing one of the 18 supported routers to netgear 1000. 0846 X 9040. or whatever it is(not looking at the exact spec but its accurate on the computer.) That did not work. I tried to call net gear and they haven't a clue. please help  ..... Bkratz and Co i am seriously in need of y'all  wisdom and counsel on this thing.

Thx


DOgwu

---

### Post by RedSingularity on 2010-03-18
Which Ubuntu version are you using?

---

### Post by odogwu on 2010-03-19
Ubuntu 9.10

---

### Post by RedSingularity on 2010-03-19
Is it a PCI card?  
If so Post the output of 

lspci

---

### Post by odogwu on 2010-03-20
Hi sorry this is the output i got after further reading. It is a USB card.


lsusb

Bus 001 Device 005: ID 0846:9040 NetGear, Inc. 
Bus 001 Device 003: ID 054c:00ee Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chibuzor@chibuzor-desktop:~$ 


chibuzor@chibuzor-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth1
       version: 02
       serial: 00:0d:56:8b:3f:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
chibuzor@chibuzor-desktop:~$ 


What do I do next?

---

### Post by RedSingularity on 2010-03-20
The chipset is not showing up for that model.  Do you know the chipset model?

Post the output of 

iwconfig

---

### Post by odogwu on 2010-03-23
thanks for your help with this. I really appreciate it.

iwconfig says


lo  no wireless extensions

eth1 no wireless extensions

pan0 no wireless extensions

?/
dont know what else to do when i switch over to windows i'm good togo on wireless

---

### Post by RedSingularity on 2010-03-23
What is the chipset model?  It should say on the device itself.

---

### Post by odogwu on 2010-03-25
Hi,

These are all the numbers on the device.
If you know where i can find it while in windows let me know


FCC ID. PY308100079
IC: 4054A-08100079
MAC:0024B2574579

THIS IS ANOTHER RANDOM NUMBER ON THE DEVICE WITHOUT A NAME 272-10859-01

---

### Post by chili555 on 2010-03-25
> Bus 001 Device 005: ID [COLOR="Blue"]0846:9040[/COLOR] NetGear, Inc. 

Please see: [http://ubuntuforums.org/showpost.php?p=8828250&postcount=14](http://ubuntuforums.org/showpost.php?p=8828250&postcount=14)> static struct usb_device_id ar9170_usb_ids[] = {
/* Atheros 9170 */
{ USB_DEVICE(0x0cf3, 0x9170) },
/* Netgear WNA1000 */
{ USB_DEVICE(0x[COLOR="Blue"]0846[/COLOR], 0x[COLOR="Blue"]9040[/COLOR]) },
/* TP-Link TL-WN821N v2 */
{ USB_DEVICE(0x0cf3, 0x1002) },


---

