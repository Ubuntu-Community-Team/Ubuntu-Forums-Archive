---
title: "Wireless USB Adapter"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by doubad on 2009-07-02
So i bought a cheap COMstar Wireless N router & USB Adapter Kit. My desktop is running Jaunty and it doesn't seem to notice the USB adapter. Any suggestions?

---

### Post by philcamlin on 2009-07-02
whats the model ?

---

### Post by doubad on 2009-07-02
CO-NPWL-NBUN

[http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10110734&catid=](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10110734&catid=)

---

### Post by superprash2003 on 2009-07-03
post output of
1)lusb
2)lshw -C network

---

### Post by doubad on 2009-07-03
I think it's detecting the wired network card built in to the motherboard.

lusb
bash: lusb: command not found

lshw -C network

WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 88E8001 Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: a
bus info: pci@0000.00.0a.0
logical name: eth0
version: 13
serial: 00:13:d4:de:3c:78
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast-yes driver-skge driverversion-1.13 firmware=N/A
latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 1e:1b:d5:5e:14:97
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
multicast=yes

---

### Post by doubad on 2009-07-04
anyone?
has anyone used a wireless usb adapter and been successful?

---

### Post by riccardo on 2009-07-05
Hi there,

I have a "Sagem" brand usb dongle ... that modern linuxes just find and work thru!!  It is a model 'XG 760G' ...and I got it  off eBay from a merchant in China.  Very cheap, nothing to adjust ... it just works.  Try searching for 'usb wifi card' dongle or similar.  Postage to Australia was no problem.  Deal with well-regarded merchant.

riccardo

---

### Post by RedSingularity on 2009-07-05
Look [here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) for supported devices.

---

### Post by linuxyousertoetags on 2010-01-09
i also haveone of these and am running karmaic is there any way to get drivers for linux for this?

---

### Post by pdc on 2010-01-10
> i also haveone of these

if we assume that you mean you have a

> cheap COMstar Wireless N router & USB Adapter Kit. 

?????????????????????

open a terminal

type

> lsusb

copy and paste the result back here

---

### Post by linuxyousertoetags on 2010-01-13
typed in lsusb and got this: 

Bus 001 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse

Bus 005 Device 002: ID 1241:1503 Belkin Keyboard

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the realtek one is the comstar wireless n  usb adapter

---

### Post by linuxyousertoetags on 2010-01-14
i dont have the modem, just the dongle it works on windows just fine with my buddys d-link router \, the dongle model # is co-npwl-nusb

---

