---
title: "Installing Wifi Drivers in 12.04 without Ethernet"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by nekollx on 2012-10-20
I have A Unbutu box and the drivers (copied from the device DVD, and they are Linux drivers) But i can't figure out how to get them into the system so the adapter will be detected and activated

---

### Post by mikewhatever on 2012-10-21
You might want to elaborate (quite a bit really) on what wifi devices are there, and what exactly was on the DVDs. 
Drivers are often provided with the README file that tells you how to install them.

---

### Post by Bucky Ball on 2012-10-21
Welcome.

Open a terminal (Applications>Accessories>Terminal) and paste this in:

```
sudo lshw -C network
```Post the result back here, please.

---

### Post by nekollx on 2012-10-21
> **mikewhatever said:**
> You might want to elaborate (quite a bit really) on what wifi devices are there, and what exactly was on the DVDs. 
Drivers are often provided with the README file that tells you how to install them.

its a realteck rt5370 v20

I saw a read me but couln't really get heads or tails out of it, sorry I'm a Unbutu noob

---

### Post by Bucky Ball on 2012-10-21
> **Bucky Ball said:**
> Welcome.

Open a terminal (Applications>Accessories>Terminal) and paste this in:

```
sudo lshw -C network
```Post the result back here, please.

Waiting ...

---

### Post by nekollx on 2012-10-21
> **Bucky Ball said:**
> Waiting ...

System was acting up last night

Um all it's returning is PCI (sysfs)

---

### Post by varunendra on 2012-10-21
> **nekollx said:**
> System was acting up last night

Um all it's returning is PCI (sysfs)
Just wait a few sec. and it will return a lot of things :)

In addition to lshw, please also post outputs of :
```
lspci -nnk | grep -iA2 net
lsmod
```

If it is a USB adapter, then also post the output of :
```
lsusb
```

---

### Post by Bucky Ball on 2012-10-21
> **varunendra said:**
> Just wait a few sec. and it will return a lot of things :)



+1. Give it a chance to think ...

---

### Post by nekollx on 2012-10-21
*-network               
       description: Ethernet interface 
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet 
       vendor: Davicom Semiconductor, Inc. 
       physical id: b 
       bus info: pci@0000:02:0b.0 
       logical name: eth1 
       version: 31 
       serial: 00:08:a1:10:d9:16 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=32 link=no maxlatency=40 mingnt=20 multicast=yes 
       resources: irq:23 ioport:d800(size=256) memory:ff9efc00-ff9efcff memory:ff980000-ff9bffff 
  *-network:0 
       description: Wireless interface 
       physical id: 1 
       bus info: usb@1:2 
       logical name: wlan2 
       serial: 7c:dd:90:12:4a:d6 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-29-generic-pae firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn 
  *-network:1 
       description: Wireless interface 
       physical id: 2 
       bus info: usb@1:1.3 
       logical name: wlan1 
       serial: 00:0d:3a:23:c3:fc 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=prism2_usb driverversion=3.2.0-29-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11b

---

### Post by Bucky Ball on 2012-10-22
Unplug the other wireless USB. That could confuse the issue. 

[QUOTE=nekollx]its a realteck rt5370 v20[/QUOTE]

Your output shows you have this driver installed:

```
driver=rt2800usb driverversion=3.2.0-29-generic-pae firmware=0.29
```Anyhow, the Realtek USB has drivers loaded already but it may be the incorrect one. Try the following link, the fourth one down the list is the Linux driver for your card. Click it and fill in your details. The file will download and there should be a Readme in there to 'make' 'make install' etc ... 

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

 If no joy, try and give us some more info about your setup: You are not picking up any wireless networks? Are you going through a router/access point?

---

