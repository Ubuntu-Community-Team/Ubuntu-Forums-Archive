---
title: "D-Link DSL-210 ADSL USB Modem"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by medorpg on 2009-03-10
Hi, It's my first post and it been a while since I used linux

So as far as I remember I had a problem with my USB modem
D-Link DSL-210

and I was asking if its now supported or anyone was able to get it work on Ubuntu

---

### Post by khelben1979 on 2009-03-10
```
lusb
```
will give us a better picture of the hardware.

---

### Post by Neo_The_User on 2009-03-10
dmesg too would show all USB devices as well.

---

### Post by medorpg on 2009-04-21
Sorry for replying a little late ;)

Actually right now im using windows and before I used linux ( Suse ) and wasnt able to get my modem works but that was since Suse 9 and now im thinking of moving to linux again and im waiting for ubuntu 9.04

So is theres any software that gives you the same information of lusb but for windows ?

Or tell me whatever you need but take in consideration that im using windows right now

Thanks so much
and really hope it works

---

### Post by khelben1979 on 2009-04-22
Go to the D-Link homepage and look for drivers.

---

### Post by medorpg on 2009-04-22
Actually theres a problem with the linux shipment driver and seems like they dont support this device any more

anyway I was managed to get this

root@darkstar:~# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0572:cb00 Conexant Systems (Rockwell), Inc.
Bus 001 Device 003: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+


in the worst case I'll download ubuntu 9.04 and try if it detects it and if not I'll buy an ethernet device better than this pain

---

### Post by khelben1979 on 2009-04-23
> **medorpg said:**
> Actually theres a problem with the linux shipment driver and seems like they dont support this device any more

Actually, I was more thinking of the D-Link driver for Windows (if they have one).

Ethernet modems are easier detected by Linux according to what I have read on different sources.

---

### Post by medorpg on 2009-04-23
Okay I have its driver for windows and its working fine on windows

and here is the latest news
on ubuntu 9.04 ( I ran it as a live cd )

i performed the lsusb command

and the result was my usb devices and one of them is

Conexant Systems (Rockwell) Inc. E-Tech ADSL Modem V2


PLEASE HELP ME ](*,)

---

### Post by medorpg on 2009-04-23
Here's the direct download link for the driver (Both windows and linux)

[ftp://ftp.dlink-me.com/DLink_ME/ADSL/DSL-210/Drivers/DSL_210_Driver.zip](ftp://ftp.dlink-me.com/DLink_ME/ADSL/DSL-210/Drivers/DSL_210_Driver.zip)

---

### Post by medorpg on 2009-04-24
Is it that hard to support USB Modems on linux :S ?????

Please send me any tutorial to follow or anything

---

### Post by khelben1979 on 2009-04-24
Okay, [check out this thread]("http://www.linuxforums.org/forum/linux-newbie/53135-usb-adsl-modem-dlink-dsl-210-a.html"). Maybe it can help?

---

### Post by medorpg on 2009-04-24
Thank you for your help and I will try this tutorial and tell you if it worked or not

Really you've been a great help for me thank you again

---

