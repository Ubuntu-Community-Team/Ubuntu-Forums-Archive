---
title: "no wifi on dell precision m2400"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by velt on 2011-04-13
Hi, since installation I dont have any wifi on a dell precision m2400, I have installed ubuntu 64bits. 
Please help.

---

### Post by matt-fender on 2011-04-13
What version of Ubuntu are you running, now that you have it running? :cool:

EDIT: Nevermind, Just seen your last thread, 10.10

Can you open a Terminal 

Applications > Accessories > Terminal

and paste the following

```
iwconfig
```then hit enter

Does it show any wireless devices attached?

also could you paste the output of 

```
lspci
```

We can get your exact wireless device this way

---

### Post by velt on 2011-04-13
> **matt-fender said:**
> What version of Ubuntu are you running, now that you have it running? :cool:

EDIT: Nevermind, Just seen your last thread, 10.10

Can you open a Terminal 

Applications > Accessories > Terminal

and paste the following

```
iwconfig
```then hit enter

Does it show any wireless devices attached?

also could you paste the output of 

```
lspci
```We can get your exact wireless device this way

iwconfig
lo   no wireless extensions
eth0   no wireless extensions

velt@velt-Precision-M2400:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [Quadro FX 370M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
velt@velt-Precision-M2400:~$

---

### Post by matt-fender on 2011-04-13
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Super, thanks for confirming that. Do you have access to wired internet? If you do you could simply go to System > Administration > Additional Drivers and install the Broadcom drivers for your wireless.

---

### Post by velt on 2011-04-13
> **matt-fender said:**
> 0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Super, thanks for confirming that. Do you have access to wired internet? If you do you could simply go to System > Administration > Additional Drivers and install the Broadcom drivers for your wireless.

I will go wired and try it out now. 
Thanks.

---

### Post by PCNetSpec on 2011-04-13
Connect to your router with an ethernet cable, then open a terminal and enter:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

Then go to System>Administration>Additional Drivers and activate the STA driver.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by matt-fender on 2011-04-13
> **velt said:**
> I will go wired and try it out now. 
Thanks.

No problem, if it doesn't show up straight away try performing some updates.

System > Administration > Update Manager

---

### Post by PCNetSpec on 2011-04-13
Sorry **matt-fender**, didn't see your response there.

---

### Post by matt-fender on 2011-04-13
> **PCNetSpec said:**
> Sorry **matt-fender**, didn't see your response there.

No problem, everyone's here to help! good to see some Linux love in Cornwall btw, I thought i was alone down here!

---

### Post by PCNetSpec on 2011-04-13
Heh... nah, there are a few of us :)

---

### Post by velt on 2011-04-13
> **matt-fender said:**
> 0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Super, thanks for confirming that. Do you have access to wired internet? If you do you could simply go to System > Administration > Additional Drivers and install the Broadcom drivers for your wireless.

worked great. I still have thousands of details like why it doesnt resume when opening the lid but having wifi is a start.

---

### Post by matt-fender on 2011-04-13
> **velt said:**
> worked great. I still have thousands of details like why it doesnt resume when opening the lid but having wifi is a start.


Awesome! wifi is a great start :)

---

