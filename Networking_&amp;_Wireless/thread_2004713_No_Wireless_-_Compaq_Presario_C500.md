---
title: "No Wireless - Compaq Presario C500"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by fidgaf on 2012-06-16
Installed Ubuntu 12.04 on my Compaq Presario C500 using Windows Installer. I do also have a burned 12.04 disc which has been fine on other laptops.

It's not finding/detecting wireless.

Some message about a firmware problem and, very cleverly, showed a new icon in the top right about installing something.

Not so clever, it wanted to connect to the Internet to replace/install the thing that I need to connect to the Internet. :o)

That green icon has now gone.

A) What do I do to find out what wireless widget Ubuntu thinks is installed?

C) How do I find the files needed?

B) How can I download/install the firmware/driver/whatever that it needs without an Internet connection?

Thanks.

I need an idiot guide as similar problems I've seen are totally incomprehensible or impossible to follow.

e.g. "....System > Administration > Synaptic Package Manager >......" . I used to know where these were before (nice menu) but seemed to have disappeared in 12.04.

so pretend I know nothing and you won't go far wrong.

Thanks.

:oD


.

---

### Post by fidgaf on 2012-06-16
Update:
It seems to be hunting for a "Broadcom STA wireless driver"..... on the Internet :) when I look in "System Settings > Additional Drivers".

I still have no idea what I have installed.

Compaq/HP spec sheet says:
Wireless Technologies
C556CA: 802.11b/g WLAN

But I would like Ubuntu to tell me itself.

---

### Post by fidgaf on 2012-06-16
Some vaguely related forum seemed to think this helps:

lspci Output
============

lspci -nnm

```
linlin@ubuntu:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [27a0]" -r03 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [27a2]" -r03 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [27a6]" -r03 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "N10/ICH 7 Family High Definition Audio Controller [27d8]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "N10/ICH 7 Family PCI Express Port 1 [27d0]" -r01 "" ""
00:1c.2 "PCI bridge [0604]" "Intel Corporation [8086]" "N10/ICH 7 Family PCI Express Port 3 [27d4]" -r01 "" ""
00:1d.0 "USB controller [0c03]" "Intel Corporation [8086]" "N10/ICH 7 Family USB UHCI Controller #1 [27c8]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1d.1 "USB controller [0c03]" "Intel Corporation [8086]" "N10/ICH 7 Family USB UHCI Controller #2 [27c9]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1d.2 "USB controller [0c03]" "Intel Corporation [8086]" "N10/ICH 7 Family USB UHCI Controller #3 [27ca]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1d.7 "USB controller [0c03]" "Intel Corporation [8086]" "N10/ICH 7 Family USB2 EHCI Controller [27cc]" -r01 -p20 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re1 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801G (ICH7 Family) IDE Controller [27df]" -r01 -p8a "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [27c5]" -r01 -p01 "Hewlett-Packard Company [103c]" "Device [30a5]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "N10/ICH 7 Family SMBus Controller [27da]" -r01 "Hewlett-Packard Company [103c]" "Device [30a5]"
06:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Hewlett-Packard Company [103c]" "BCM4311 802.11b/g Wireless LAN Controller [1364]"
08:08.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Hewlett-Packard Company [103c]" "Device [30a5]"
linlin@ubuntu:~$ 


```


Terminal into gedit, onto pendrive, onto MS PC to here. :D

"BCM4311" **is** listed in the driver(s) mentioned above - That's a good thing I think, if I'm looking at the right bit here.

I'm now out of things I can think of to do.



.

---

### Post by fidgaf on 2012-06-16
saw this linked but it makes little sense to me and just sounds scary.

It may help someone with brains that is trying to help:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by fidgaf on 2012-06-22
*Bump*

Anyone?

Please.:confused:

---

### Post by fidgaf on 2012-06-22
Did this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Read carefully, particularly the Ubuntu bits and have an Internet connected PC and a pendrive handy. Make sure you follow the "No Internet Access" parts. I dumped the first file on **desktop** and the others in **home**

The "activate" bit didn't seem to work but pressed the buttons anyway, ignored it and restarted.

IT WORKS!!!!! :guitar:

Thanks for everyone's help. :tongue: :D

I hope this helps someone else.

---

### Post by ejcottier on 2012-09-27
How rude, no one replied to you :/

Well I have the same problem as you did, wireless won't work out of the box. But I have managed to connect automatically with a TP-Link wireless usb dongle. 


I'll try the steps you took :) 

And by the way, is ubuntu painfully slow on your c500? I was wondering whether it was because it was installed through windows...

I'm running LXDE it's that slow lol

UPDATE:

I tried installing the STA drivers and I realised I already had them installed.. and they DON'T work.

I installed the b43 drivers: sudo apt-get install firmware-b43-installer

And removed the STA drivers: sudo apt-get remove bcmwl-kernel-source

And then I rebooted, and BINGO, it works :D


I'm just gonna add that the b43 drivers DON'T show up in the 'Additional Drivers', but they are still there, and they still work :D

---

### Post by fidgaf on 2012-09-28
> **ejcottier said:**
> 
And by the way, is ubuntu painfully slow on your c500? I was wondering whether it was because it was installed through windows...

No, Ubuntu works nice and fast. Quick boot and no problems running my usual programs.

The exact opposite of XP that now seems too bloated to work well.

---

