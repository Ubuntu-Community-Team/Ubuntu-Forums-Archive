---
title: "Retail Plus+ Wireless N Adaptor"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by dbwrobel on 2011-05-19
Hi, I've just started playing with Ubuntu for the first time and loaded up 10.04.2 LTS (64bit). After starting up the machine though my wireless doesn't appear to be working and I have no other way to connect to the Internet.

*Tried by installing ndiswrapper,ndisgtk,etc and using windows xp x64 driver - it would install the driver and say hardware was detected but would take a very long time to login (and give me an error about the power manager from what I remember) - is it possible maybe that I should try a 32 bit driver that came on the cd? (net8192su.inf)

*Tried by installing the b43 driver/firmware method on the ubuntu site (offline) - could not turn on the driver in "Additional Hardware"
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
or
[http://linuxforums.org.uk/linux-tips-tricks/offline-install-of-b43-fwcutter-and-firmware-for-broadcom-wireless-devices/](http://linuxforums.org.uk/linux-tips-tricks/offline-install-of-b43-fwcutter-and-firmware-for-broadcom-wireless-devices/)

*Tried by installing the sta driver/firmware method on the ubuntu site (offline) - could not turn on the driver in "Additional Hardware"
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
or
[http://linuxforums.org.uk/linux-tips-tricks/offline-install-of-b43-fwcutter-and-firmware-for-broadcom-wireless-devices/](http://linuxforums.org.uk/linux-tips-tricks/offline-install-of-b43-fwcutter-and-firmware-for-broadcom-wireless-devices/)

So...after all that I think I am totally lost :(

---

### Post by chili555 on 2011-05-19
Something's wacky. I highly doubt that net8192su.inf and b43 and firmware are correct for the same hardware. We need to determine if you have a Broadcom device or a Realtek device. Please open a terminal and run:```
lspci -nn
```Post the line that corresponds to your wireless device and Dr. Chili will do a CT scan and help this patient.

If this is a USB device, instaed post:```
lsusb
```

---

### Post by dbwrobel on 2011-05-19
Thanks for the quick reply :) I hope the CT scan helps lol

I don't think its listed under the pci scan but I do get it to appear using 'lsusb'

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 12)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 12)
00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 12)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 12)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 12)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 12)
00:14.3 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers [8086:3438] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV620 LE [Radeon HD 3450] [1002:95c5]
02:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
04:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
04:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

lsusb:

Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp.

---

### Post by dbwrobel on 2011-05-19
Just found a new link I noticed that its 8172 in lsusb and not 8192 like the driver says; trying

[http://ubuntuforums.org/showthread.php?t=1353049](http://ubuntuforums.org/showthread.php?t=1353049)

---

### Post by chili555 on 2011-05-19
> Bus 002 Device 002: ID 0bda:8172 [COLOR="Red"]Realtek[/COLOR] Semiconductor Corp.> *Tried by installing the b43 driver/firmware method on the ubuntu site (offline) - could not turn on the driver in "Additional Hardware"
[https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx)It doesn't appear that Broadcom drivers will help us.

Are you in love with 10.04 LTS; really, really in love? In love enough to suffer??

The newest release 11.04 has the driver built in!```
$ modinfo r8712u | grep 8172
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8172[/COLOR]d*dc*dsc*dp*ic*isc*ip*

```If you want the driver in 10.04 LTS, we'll need to download the driver, kernel headers and build tools, gcc, make, etc.; all with no internet connection.

Is it impossible? Nope. Is it very hard? Yep. I will be anxious to help you with either method; after all it's not my equipment.

What do you prefer?

---

### Post by dbwrobel on 2011-05-19
haha I think I will dump lucid for natty it if its thats the case :P

Thanks for your help!

---

### Post by chili555 on 2011-05-19
Try the live CD and see if the wireless doesn't spring to life; if you like it, install it.

---

### Post by dbwrobel on 2011-05-19
just tried with the live cd with natty and wireless is now alive and kicking :)

Thanks!

---

