---
title: "Wireless Adapter Help Needed - On My Last Legs Here"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by Jonj1611 on 2011-03-14
Hi,

I have installed Ubuntu 10.10, its a computer I built for my daughter, I chose Linux as I thought it would be a safer option for her, however for the life of me I cannot get the usb wireless working, I have been through numerous forums and I just can't get it to work.

The device is a MicroNext mn-wj546j, I believe it uses RaLink RT2070

Anyway I tried it first of all with ndiswrapper, ndiswrapper says its found the hardware and installed the drivers, but I cannot see any wireless device in the network manage and ndiswrapper throws up loads of unknown symbol errors in its log.

I ran lsusb and here is the result :-

jon@CaitlinsPC:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 062a:0102 Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

To be honest I am completely lost in Linux so any help on what my next steps should be would be gratefully received as I am pulling my hair out here.

Thanks :)
Jon

---

### Post by chili555 on 2011-03-14
Please run and post:```
ndiswrapper -l
cat /etc/modprobe.d/blacklist
```This should go quickly and easily.

---

### Post by Jonj1611 on 2011-03-14
Hi,

Many thanks for your help, I was trying to follow another thread you helped someone out in but got a bit lost, hence why in my blacklist file the current wired network device is blacklisted, anyway here are the results :-

[PHP]jon@CaitlinsPC:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netr28u : driver installed
	device (148F:2070) present[/PHP]

[PHP]jon@CaitlinsPC:~$ cat /etc/modprobe.d/blacklist.conf
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
blacklist e100
jon@CaitlinsPC:~$ [/PHP]

Thank you again :)
Jon

---

### Post by chili555 on 2011-03-14
> netr28u : driver installed
    device (148F:2070) present  Looks pretty healthy, actually. Now let's see:```
lsmod | grep -e ndis -e rt2
iwconfig
```Thanks.> jon@CaitlinsPC:~$ cat /etc/modprobe.d/blacklist.conf That's not what I asked for:> cat /etc/modprobe.d/blacklist

---

### Post by Jonj1611 on 2011-03-14
Hi,

Many thanks for replying, here is the info you requested :-

> jon@CaitlinsPC:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory

> jon@CaitlinsPC:~$ lsmod | grep -e ndis -e rt2
ndiswrapper           184207  0 

> jon@CaitlinsPC:~$ iwconfig
lo        no wireless extensions.

Hope it means more to you lol

Jon

---

### Post by chili555 on 2011-03-14
Before we put on our geek glasses and go medieval, check this, please:```
sudo rmmod -f ndiswrapper
sudo modprobe rt2870sta
iwconfig
```Thanks.

---

### Post by Jonj1611 on 2011-03-14
Hi,

Ok sudo rmmod -f ndiswrapper just asked for my password and returned to the prompt.

> jon@CaitlinsPC:~$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

> jon@CaitlinsPC:~$ iwconfig
lo        no wireless extensions.

Hope that helps?

Jon

---

### Post by chili555 on 2011-03-14
Now, before you reboot or do anything else, please let me see:```
dmesg | grep rt2
modinfo rt2870sta | grep -e version -e 2070
```

---

### Post by Jonj1611 on 2011-03-14
Hi,

> jon@CaitlinsPC:~$ dmesg | grep rt2
[ 6515.847791] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 6515.856221] usbcore: registered new interface driver rt2870

> jon@CaitlinsPC:~$ modinfo rt2870sta | grep -e version -e 2070
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 

Regards
Jon

---

### Post by chili555 on 2011-03-14
> vermagic: 2.6.35-[COLOR="Red"]22[/COLOR]-generic SMP mod_unload modversions 686 Ah, ha! Now it makes sense. Your RT2070 device is not covered until the kernel version just after -22.

If you have a wired ethernet internet connection, you could go to System > Administration > Synaptic. Search for linux-image. Look for the latest, 2.6.35-27 and install it. Then do:```
sudo ndiswrapper -e netr28u
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit.

Reboot and your wireless should be working.

---

### Post by Jonj1611 on 2011-03-14
Hi,

Will do that know and report back.

Thank you for all your help
Jon

---

### Post by Jonj1611 on 2011-03-14
I done what you said but nothing is showing under wireless networks still?

Regards
Jon

---

### Post by chili555 on 2011-03-14
Please run and post:```
sudo modprobe rt2870sta
dmesg | grep rt2
modinfo rt2870sta | grep -e version -e 2070
```We'll get to the bottom of this...

---

### Post by Jonj1611 on 2011-03-14
Hi,

Thanks for sticking with me on this, ok so here are the results :-

> jon@CaitlinsPC:~$ sudo modprobe rt2870sta
[sudo] password for jon: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

> jon@CaitlinsPC:~$ dmesg | grep rt2
[ 1033.373120] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1033.382575] usbcore: registered new interface driver rt2870
[ 1034.164173] <==== rt28xx_init, Status=0
[ 1035.142969] <==== rt28xx_init, Status=0

> jon@CaitlinsPC:~$ modinfo rt2870sta | grep -e version -e 2070
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.35-27-generic SMP mod_unload modversions 686 

Regards
Jon

---

### Post by chili555 on 2011-03-14
We're closer!```
lsmod | grep -e ndis -e rt2
iwconfig
```> jon@CaitlinsPC:~$ modinfo rt2870sta | grep -e version -e 2070
version: 2.1.0.0
srcversion: 93E93E3E336F412601AF0FA
alias: usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
vermagic: 2.6.35-27-generic SMP mod_unload modversions 686 Excellent!

---

### Post by Jonj1611 on 2011-03-14
Hmm, well the oddest thing, I went downstairs to the linux box and it said wireless connections, clicked on it and saw my router, typed password and connected!!! 

It wasnt there just now I swear, so it all seems to be working, thank you very much Chili for you help and sticking with me on this one, really appreciated and my daughter will be over the moon.

Thanks again :)
Jon

---

### Post by Jonj1611 on 2011-03-14
Hmm, well that was short lived, the computer done some updates, system updates I believe, rebooted and now the wireless has gone again.

Anyway here is the info you requested :-

> jon@CaitlinsPC:~$ lsmod | grep -e ndis -e rt2
ndiswrapper           184207  0 

> jon@CaitlinsPC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Dont know if thats any help or not ?

Regards
Jon

---

### Post by chili555 on 2011-03-14
Please do:```
sudo su
apt-get remove --purge ndiswrap*
echo rt2870sta >> /etc/modules
modprobe rt2870sta
exit
```Any improvements?

---

### Post by Jonj1611 on 2011-03-14
Hi, Yep that worked thank you :) Loads first time everytime, thank you so much for your help :)

Regards
Jon

---

