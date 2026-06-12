---
title: "HUAWEI E169 modem, can't connect"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Raymond Curtis on 2009-11-18
Hello folks.

I am using Ubuntu 9.10 and I've configured my mobile broadband network.
I've chosen my internet provider from the list, however I can't connect to the internet.
Modem is on USB, it is mounted properly but I don't know if it is detected properly. How to check that?

When I was configuring mobile connection via Network Manager wizzard, on the first screen I could not chose my device (the list was grayed out and it was displaying "any device").

Thanks for your time.

---

### Post by alexfish on 2009-11-18
goto  applications/accessories/terminal

type in

lsusb

---

### Post by Raymond Curtis on 2009-11-18
Thank you alexfish for such quick reply.

Here is the list of my USB devices:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


As you see it detects model E620 which is not true because I have for sure E169.
But does it have any matter?

**Edit:**

I was searching for more clues on the Internet and my not working hardware is an error in the kernel.
So I wanted to update my kernel. I've downloaded this package:

linux-image-2.6.31-16-generic_2.6.31-16.50lp446146apw5_i386.deb

But it doesn't want to install. I am getting this error:

Error: Wrong architecture 'i386'

Linux kernel image for version 2.6.31 on x86/x86_64
This package contains the Linux kernel image for version 2.6.31 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 

I don't understand this. My processor is Intel Core Duo 2 and I am working on Dell laptop.

Thanks for any help.

---

### Post by pdc on 2009-11-19
can't comment on the kernel update

but try post #2 here

[http://ubuntuforums.org/showthread.php?t=1305931&highlight=vodafone](http://ubuntuforums.org/showthread.php?t=1305931&highlight=vodafone)

for your modem:

The 169 has the ID  you quote; and gets called E620

---

### Post by alexfish on 2009-11-19
> **Raymond Curtis said:**
> Hello folks.

I am using Ubuntu 9.10 and I've configured my mobile broadband network.
I've chosen my internet provider from the list, however I can't connect to the internet.
Modem is on USB, it is mounted properly but I don't know if it is detected properly. How to check that?

When I was configuring mobile connection via Network Manager wizzard, on the first screen I could not chose my device (the list was grayed out and it was displaying "any device").

Thanks for your time.
usb-modeswitch may help

can be installed via synaptic version 1.0.2-1

lastest version  1.0.5.

can be downloaded at this site gives the pro and cons and how to cofig the device

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

main site  download link

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

keep a copy on a usb stick

it may not cure your problem but it may help

added
 on the kernel issue is the system upgraded or clean / fresh install .

---

### Post by cavh on 2009-11-19
Try two things:

1. update your modem firmware by browsing the support section on the website of your mobile operator. You will unfortunately need access to a Windows machine for this.

2. disable the 'boot from USB' option in your BIOS.

These two steps seem to have resolved my issue with my Huawei E17X on the T-Mobile network here in the UK (using Karmic Koala 9.10 with kernel version 2.6.31-14-generic).

---

