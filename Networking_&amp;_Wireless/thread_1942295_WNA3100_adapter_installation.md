---
title: "WNA3100 adapter installation"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by marian0700 on 2012-03-17
Hi all!,
I am a new member of this forum. I have installed on my Samsung nc10 Ubuntu 10.04. I want to use my Netgear WNA3100 wifi adapter with my netbook. But it seems the driver instalation is not so easy like I thought. Can anybody help my with this, and write step by step where to find correct drivers and how to install it to make this adapter works.

When I run in terminal lsusb:
laszki@laszki-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 003: ID 174f:5933 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2012-03-17
See post #29 here: [http://ubuntuforums.org/showthread.php?t=1695036&page=3](http://ubuntuforums.org/showthread.php?t=1695036&page=3)

This is valid if yours is a 32-bit system; is it?

Post back if you get stuck.

---

### Post by marian0700 on 2012-03-17
Installation run well. But still doesn't work. When i run in terminal ndiswrapper -l i got :
bcmwlhigh5 : driver installed
    device (0846:9020) present

adapter still not working. 

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 004: ID 174f:5933 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2012-03-17
I dont know if it is the same driver like this:

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

This one (and maybe the other, too) does not work with dualband/N-mode. You may need to change the mode settings in your router to b+g only

---

### Post by marian0700 on 2012-03-17
Whait a minute... I'm trying to install drivers for netgear adapter to use N standart. And now Your are telling me that I'm installing an adapter which does not work in N standard? Ehh... 
That's the reason why I want to install it, to work in N standard. The wifi card (build-in ) normally work on ubuntu, so I wanted to use Netgear adapter.

I will try to use driver from last post.

---

### Post by marian0700 on 2012-03-17
Despite of installed drivers still does not work.

bcmn43xx32 : driver installed
    device (0846:9020) present
bcmwlhigh5 : driver installed
    device (0846:9020) present

Any ideas?

---

### Post by chili555 on 2012-03-17
> [COLOR="Red"]bcmn43xx32[/COLOR] : driver installed
device (0846:9020) present
[COLOR="Red"]bcmwlhigh5[/COLOR] : driver installed
device (0846:9020) presentThe two .inf files are likely conflicting; the trick is to find which needs removal. Please post:```
dmesg | grep ndis
```Thanks.

---

### Post by marian0700 on 2012-03-17
what should I do no?

laszki@laszki-laptop:~$ dmesg | grep ndis
[   12.066161] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.748618] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   12.749365] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   12.750542] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   12.809926] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2012-03-17
I would try this:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwlhigh5
```Now reboot and let us see:```
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by marian0700 on 2012-03-17
ndiswrapper -l
bcmn43xx32 : driver installed

dmesg | grep ndis
[   12.149232] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.395284] usbcore: registered new interface driver ndiswrapper
[  257.819115] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded

---

### Post by praseodym on 2012-03-17
The problem is the Broadcom chipset. For Broadcom-USB devices there is sadly no linux driver. The Windows driver with ndiswrapper doesnt handle N-mode.

---

### Post by marian0700 on 2012-03-17
too bad. Ok, thank U all very much for help.

---

### Post by praseodym on 2012-03-17
IMHO it does not work in **dualband**, i.e. 5 GHz region. It may work in the lower 2.4 GHz band, but there is only up to 150 M in the very best way.

---

### Post by chili555 on 2012-03-17
> ndiswrapper -l
bcmn43xx32 : driver installedWe wonder why it doesn't report "Device present" as before:> bcmn43xx32 : driver installed
device (0846:9020) presentWas the device inserted at the time? I believe the .inf is correct for your device:> <snip>
[Manufacturer]

%Broadcom% = Broadcom



[Broadcom]

%BCM4xx01_DeviceDesc% = BCM43XXN32, USB\VID_050D&PID_825C

%BCM4xx02_DeviceDesc% = BCM43XXN32, USB\VID_050D&PID_6050

%BCM4xx04_DeviceDesc% = BCM43XXN32, USB\VID_050D&PID_615A

%BCM4xx03_DeviceDesc% = BCM43XXN32, USB\VID_0846&PID_9011

%BCM4xx03_DeviceDesc% = BCM43XXN32, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9020[/COLOR]



[BCM43XXN32]

Characteristics	= 0x84	

BusType		= 15	

AddReg		= Parameter

CopyFiles	= Driver
<snip>May we see:```
ls /etc/ndiswrapper
```We may need to do some cleanup.

---

