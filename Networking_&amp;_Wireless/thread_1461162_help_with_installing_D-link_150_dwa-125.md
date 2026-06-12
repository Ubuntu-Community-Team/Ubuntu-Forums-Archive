---
title: "help with installing D-link 150 dwa-125"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by jr0535 on 2010-04-23
so im a newbie at this ubuntu stuff so tell me what to do slowly =)

ive read many threads about getting to work and tried many things but just cant seem to make it work... so help =)

since i saw this on most of threads ive read ill post it

Ubuntu 9.10
and i have the driver disk for windows

```
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 07d1:3c0d D-Link System 
Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```thank you very much :)

---

### Post by chili555 on 2010-04-23
Please do, in a terminal:```
sudo modprobe rt2800usb
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
iwconfig
```Post the results.

---

### Post by jr0535 on 2010-04-23
```
sudo modprobe rt2800usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
``````
lsmod | grep -e rt2 -e rt3
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

``````
dmesg | grep -e rt2 -e rt3
[ 4295.556784] usbcore: registered new interface driver rt2800usb
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2010-04-23
> /etc/modprobe.d/ndiswrapperDid you try to get ndiswrapper going? Let's see: ```
ndiswrapper -l
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

### Post by jr0535 on 2010-04-23
```
ndiswrapper -l
drt2870 : driver installed
```
```
cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory
```
```
cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```

---

### Post by chili555 on 2010-04-23
> ndiswrapper -l
drt2870 : driver installedBut it doesn't report 'device present.' That's a bit mysterious. Please try:```
sudo rmmod -f rt2800usb
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by jr0535 on 2010-04-23
```
sudo rmmod -f rt2800usb
``````
sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


``````
 ndiswrapper -l
drt2870 : driver installed

``````
dmesg | grep ndis

```

---

### Post by chili555 on 2010-04-23
> drt2870 : driver installedIs this the Windows XP driver? Was there a .sys (firmware) file included in the same directory as the .inf that you installed? I am puzzled why neither ndiswrapper nor the native driver is grabbing your device.

---

### Post by jr0535 on 2010-04-23
yes that is the xp driver from the cd and there is a sys file named rt2870 with it

---

### Post by chili555 on 2010-04-23
Sorry, I will have to check in tomorrow.

---

### Post by jr0535 on 2010-04-23
alright... thxs

---

### Post by chili555 on 2010-04-24
Sorry, I was out of town until just now. 

Are you sure your device actually works? Would you please remove the device from the USB slot and open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave the terminal open and re-insert the device and see what, if any messages are written. Copy them into your reply. 

It is very mysterious that we get no activity from either ndiswrapper or the native driver in *dmesg* and no indication of what may be wrong.

---

### Post by jr0535 on 2010-04-24
```
Apr 24 18:23:02 alex-desktop kernel: [ 2109.072888] CPU1: Temperature/speed normal
Apr 24 18:23:02 alex-desktop kernel: [ 2109.076924] CPU1: Temperature above threshold, cpu clock throttled (total events = 3297)
Apr 24 18:23:02 alex-desktop kernel: [ 2109.079449] CPU1: Temperature/speed normal
Apr 24 18:23:02 alex-desktop kernel: [ 2109.088430] CPU1: Temperature above threshold, cpu clock throttled (total events = 3298)
Apr 24 18:23:02 alex-desktop kernel: [ 2109.092257] CPU1: Temperature/speed normal
Apr 24 18:30:06 alex-desktop kernel: [ 2532.668592] hub 1-0:1.0: over-current change on port 5
Apr 24 18:30:06 alex-desktop kernel: [ 2532.772015] hub 1-0:1.0: over-current change on port 6
Apr 24 18:30:06 alex-desktop kernel: [ 2532.876014] hub 1-0:1.0: over-current change on port 5
Apr 24 18:30:06 alex-desktop kernel: [ 2532.980018] hub 4-0:1.0: over-current change on port 1
Apr 24 18:30:06 alex-desktop kernel: [ 2533.084020] hub 4-0:1.0: over-current change on port 2
Apr 24 18:30:46 alex-desktop kernel: [ 2572.849974] hub 1-0:1.0: over-current change on port 5
Apr 24 18:30:46 alex-desktop kernel: [ 2572.952019] hub 1-0:1.0: over-current change on port 6
Apr 24 18:30:46 alex-desktop kernel: [ 2573.056028] hub 4-0:1.0: over-current change on port 1
Apr 24 18:30:46 alex-desktop kernel: [ 2573.160018] hub 4-0:1.0: over-current change on port 2

```

---

### Post by chili555 on 2010-04-24
> hub 1-0:1.0: over-current change on port 5
Here is a post that suggests it's a problem with the power supply for your computer: [http://www.linuxquestions.org/questions/linux-hardware-18/usb-over-current-change-killing-usb-ports-451561/](http://www.linuxquestions.org/questions/linux-hardware-18/usb-over-current-change-killing-usb-ports-451561/)

Here is another that says it may be a hardware problem, but maybe not: [http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12901.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12901.html)

Here is another interesting find: [http://www.roedie.nl/2006/08/02/hp-being-very-good-with-support/](http://www.roedie.nl/2006/08/02/hp-being-very-good-with-support/)> the over-current messages tell you that one or more USB ports are drawing more than 100mA of power. USB can deliver up to 500mA of power I believe but the connected device must ask for this.

There are AFAIK 2 reasons the kernel van generate these messages.

1. You have one or more devices connected to your USB ports that are drawing more than 500mA power.

2. You are suffering from a short circuit in you USB port(s) or on your mainbord (this is the problem that I’ve got with my laptop)

If you have devices connected to the USB ports of your server you should disconnect them one at a time and look if the messages go away. If so, then one of the devices is causing the problem.

If you do not have any USB devices connected to your server and you don’t need them you can just make sure the USB kernel modules aren’t loaded during boot or disable the USB ports in the BIOS. The over-current messages will go away.

Note: ***Do remember that something *IS* broken.*** The kernel is warning you about it and unloading the module will only stop the error messages. The over-current problem can still cause damage to your server.

Hope this helps a bit.

Regards,

SanderEmphasis added.

I am very sorry, but I believe you computer is at fault and not the wireless driver.

---

### Post by jr0535 on 2010-04-24
i did it again and i saw this...
```
Apr 24 18:51:39 alex-desktop kernel: [ 3826.356017] usb 1-6: reset high speed USB device using ehci_hcd and address 8
Apr 24 18:51:40 alex-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver drt2870
Apr 24 18:51:40 alex-desktop kernel: [ 3826.532946] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
Apr 24 18:51:40 alex-desktop kernel: [ 3826.533202] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
Apr 24 18:51:40 alex-desktop kernel: [ 3826.533855] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'
Apr 24 18:51:41 alex-desktop kernel: [ 3828.088109] usb 1-6: USB disconnect, address 8
Apr 24 18:51:42 alex-desktop kernel: [ 3829.133309] hub 1-0:1.0: over-current change on port 5
Apr 24 18:51:42 alex-desktop kernel: [ 3829.236032] hub 1-0:1.0: over-current change on port 6
Apr 24 18:51:42 alex-desktop kernel: [ 3829.340034] hub 4-0:1.0: over-current change on port 1
Apr 24 18:51:43 alex-desktop kernel: [ 3829.444019] hub 4-0:1.0: over-current change on port 2

```it says it cant load the driver

and i use the same computer on vista and the usb works fine..

---

### Post by chili555 on 2010-04-24
Does it work better with your card reader removed?

---

### Post by jr0535 on 2010-04-24
here i insert it in the first usb slot that i did the first time... then insert it in the other one that gave the other message...i think the first slot is bad but the second one looks like it is trying to load the driver
```
Apr 24 19:05:45 alex-desktop kernel: [ 4671.668015] hub 4-0:1.0: over-current change on port 2
Apr 24 19:05:47 alex-desktop kernel: [ 4673.800016] hub 1-0:1.0: over-current change on port 6
Apr 24 19:05:47 alex-desktop kernel: [ 4673.904016] hub 1-0:1.0: over-current change on port 5
Apr 24 19:05:47 alex-desktop kernel: [ 4674.008016] hub 4-0:1.0: over-current change on port 1
Apr 24 19:05:47 alex-desktop kernel: [ 4674.112018] hub 4-0:1.0: over-current change on port 2
Apr 24 19:06:11 alex-desktop kernel: [ 4697.918846] hub 1-0:1.0: over-current change on port 5
Apr 24 19:06:11 alex-desktop kernel: [ 4698.020016] hub 1-0:1.0: over-current change on port 6
Apr 24 19:06:11 alex-desktop kernel: [ 4698.124015] hub 1-0:1.0: over-current change on port 5
Apr 24 19:06:11 alex-desktop kernel: [ 4698.228018] hub 4-0:1.0: over-current change on port 1
Apr 24 19:06:11 alex-desktop kernel: [ 4698.332029] hub 4-0:1.0: over-current change on port 2
Apr 24 19:06:38 alex-desktop kernel: [ 4724.896028] usb 1-6: new high speed USB device using ehci_hcd and address 9
Apr 24 19:06:38 alex-desktop kernel: [ 4725.044820] usb 1-6: configuration #1 chosen from 1 choice
Apr 24 19:06:38 alex-desktop kernel: [ 4725.164020] usb 1-6: reset high speed USB device using ehci_hcd and address 9
Apr 24 19:06:38 alex-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver drt2870
Apr 24 19:06:38 alex-desktop kernel: [ 4725.310042] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
Apr 24 19:06:38 alex-desktop kernel: [ 4725.310299] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
Apr 24 19:06:38 alex-desktop kernel: [ 4725.311275] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'
Apr 24 19:06:50 alex-desktop kernel: [ 4736.653668] usb 1-6: USB disconnect, address 9
Apr 24 19:06:51 alex-desktop kernel: [ 4738.407806] hub 1-0:1.0: over-current change on port 5
Apr 24 19:06:52 alex-desktop kernel: [ 4738.508017] hub 1-0:1.0: over-current change on port 6
Apr 24 19:06:52 alex-desktop kernel: [ 4738.612033] hub 4-0:1.0: over-current change on port 1
Apr 24 19:06:52 alex-desktop kernel: [ 4738.716018] hub 4-0:1.0: over-current change on port 2
Apr 24 19:06:55 alex-desktop kernel: [ 4741.828306] hub 1-0:1.0: over-current change on port 5
Apr 24 19:06:55 alex-desktop kernel: [ 4741.932019] hub 1-0:1.0: over-current change on port 6
Apr 24 19:06:55 alex-desktop kernel: [ 4742.036022] hub 1-0:1.0: over-current change on port 5
Apr 24 19:06:55 alex-desktop kernel: [ 4742.140024] hub 4-0:1.0: over-current change on port 1
Apr 24 19:06:55 alex-desktop kernel: [ 4742.244025] hub 4-0:1.0: over-current change on port 2
Apr 24 19:07:03 alex-desktop kernel: [ 4749.744019] usb 1-6: new high speed USB device using ehci_hcd and address 10
Apr 24 19:07:03 alex-desktop kernel: [ 4749.892806] usb 1-6: configuration #1 chosen from 1 choice
Apr 24 19:07:03 alex-desktop kernel: [ 4750.008024] usb 1-6: reset high speed USB device using ehci_hcd and address 10
Apr 24 19:07:03 alex-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver drt2870
Apr 24 19:07:03 alex-desktop kernel: [ 4750.154107] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
Apr 24 19:07:03 alex-desktop kernel: [ 4750.154365] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
Apr 24 19:07:03 alex-desktop kernel: [ 4750.155351] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'

```

---

### Post by chili555 on 2010-04-24
Please try:```
sudo rmmod -f ndiswrapper
sudo modprobe rt2800usb
```Let's see what *syslog* has to say about that.

---

### Post by jr0535 on 2010-04-24
i had to leave sorry..

but yeah it gave me nothing for the first 1

```
 sudo modprobe rt2800usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

---

### Post by chili555 on 2010-04-25
> but yeah it gave me nothingDid it give you a wireless interface? Check with:```
iwconfig
```What does dmesg say?```
dmesg | grep rt2
```

---

### Post by jr0535 on 2010-04-25
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
 dmesg | grep rt2
[   10.076561] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
[   10.087468] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'

```

---

### Post by chili555 on 2010-04-26
I am still of the opinion that the USB port is at fault. Please remove the D-link and insert the card reader. Reboot and run:```
dmesg | grep current
```Maybe the D-link is faulty. 

We have tried both the native driver and ndiswrapper and neither wants to work properly.

---

