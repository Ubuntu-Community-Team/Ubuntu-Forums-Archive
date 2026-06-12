---
title: "ndiswrapper; installed, binded, not loading on boot"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by Dorje871 on 2010-04-11
Hello all, I'm new to forums!

My problem is that I have spent hours and hours installing ndiswrapper, finding the right windows driver (for e100 Intel), binding nsdiswrapper to driver and device, modprobing ndiswrapper, and blacklisting e100; yet when i reboot comp, e100 is still running my ethernet connection.  Cant figure it out

ndiswrapper -l:

e100bnt5 : driver installed
    device (8086:1094) present (alternate driver: e100)

lshw -C network:
*-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:68:57:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=216.158.253.148 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:5b:a5:4e:d2:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

/etc/modprobe.d/blacklist.conf:

blacklist e100 (among others it is present)

modprobe ndiswrapper gives no errors

Anyone have any suggestions?

EDIT: oh, and yes i ran:

ndiswrapper -m

---

### Post by Dorje871 on 2010-04-11
bump.

Additional info:  running Ubuntu 9.0.4

reason y i'm trying to run ndiswrapper: internet frequently spikes latency and disconnects

already loaded wcid, several other fixes

---

### Post by chili555 on 2010-04-11
> configuration: broadcast=yes [COLOR="Red"]driver=e100[/COLOR] driverversion=3.5.23-k6-NAPI firmware=N/A ip=216.158.253.148 It looks like e100 is loading anyway, despite being blacklisted. Check with:```
lsmod | grep e100
```I notice that e100 is dependent on a module *mii*. You might also blacklist *mii*.

Is ndiswrapper listed in */etc/modules*?

---

### Post by Dorje871 on 2010-04-11
ok, so i added mii to blacklist, nothing new happened after reboot.  so i checked /etc/modules and ndiswrapper is not there.

so...  do i manually add it, and does that mean that it didn't add to other places it needs to be as well?

also, if i blacklisted e100 and mii, why is this happening:

adderson@adderson-desktop:~$ lsmod | grep e100
e100                   41740  0 
mii                    13312  1 e100

still?

ps--thank you very much for help

---

### Post by chili555 on 2010-04-11
May I see your balcklist file?```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by Dorje871 on 2010-04-11
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

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist e100

blacklist mii

---

### Post by chili555 on 2010-04-11
It looks perfect. I wonder why it's loading, even though it's blacklisted. Let's try another approach:```
sudo gedit /etc/rc.local

```Add three lines:```
rmmod -f e100
rmmod -f mii
modprobe ndiswrapper
```Proofread, save and close gedit. Reboot. ndiswrapper is supposed to be written for wireless drivers, not ethernet, so we are on experimental ground here. We shall see.

---

### Post by Dorje871 on 2010-04-11
ok, so i added those 3 lines of code to rclocal and rebooted. the code worked, cause the internet connection was lost, but apparently ndiswrapper did not pick it up and start working.  so i deleted that code and rebooted in order to speak with u again!  not sure where to go from here.  I have seen IDENTICAL problems as mine (spikes of high latency and disconects) solved by ndiswrapper, including problems with the e100 driver.  Any other ideas?  and thanks again...

---

### Post by chili555 on 2010-04-11
Is ndiswrapper loading on boot?```
cat /etc/modules | grep ndis
```What does this tell us?```
sudo ethtool eth0
```

---

### Post by Dorje871 on 2010-04-11
so when i run your first command, it does nothing but give the command line again.  no errors, no nothing. when i manually LOOK at /etc/modules, there is nothing there saying ndiswrapper

when i run the ethtool:
$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x00000007 (7)
    Link detected: yes

maybe add ndiswrapper to that modules file, then add those 3 lines to the file that correctly disabled e100?

---

### Post by chili555 on 2010-04-11
> maybe add ndiswrapper to that modules file, then add those 3 lines to the file that correctly disabled e100?Yes, please, and then reboot. You know how to reverse it if it doesn't work.> so when i run your first command, it does nothing but give the command line again. no errors, no nothing.That just means the ndiswrapper declaration was not present in */etc/modules* and it should be.

---

### Post by Dorje871 on 2010-04-11
So i did those 2 things, rebooted, and connect was not there.  while in that state i ran:

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:e2:48:c5:67:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

but maybe there is another command that i could run that would give u better info about what ndiswrapper is doing in that state once e100 is disabled, and ndiswrapper is present in the modules?

---

### Post by Dorje871 on 2010-04-11
Was searching net for other windows e100 drivers, in case the one that i got was failing in ndiswrapper do to it being a 64-bit driver, etc, when i stumbled upon this reply in a thread about e100 driver issues:

				**Re: 9 to 10.0 upgrade problem e100 driver(Secret!)** 			 			 			 		  		 		 			 			Top Secret!
If your e100 network device does not work you can do one of two things:
#1 insert a dlink card (I did this for awhile)
#2 turn off ACPI in to boot loader (acpi=off)
Even SuSE does not know about this fix!

do these make sense to u?  something i could try?

---

### Post by chili555 on 2010-04-11
Let's look at these:```
ndiswrapper -l
dmesg | grep ndiswrapper
```Thanks.

---

### Post by Dorje871 on 2010-04-11
$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/kqemu, it will be ignored in a future release.
e100bnt5 : driver installed
    device (8086:1094) present (alternate driver: e100)

$ dmesg | grep ndiswrapper
[   11.717851] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.780259] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-04-11
Those look pretty normal. Does lshw still show the device as unclaimed? Did you find any other drivers to try? XP? Win2000?

---

### Post by Dorje871 on 2010-04-11
lshw only shows device as unclaimed when i remove e100 and mii.  e100 runs the connection, albeit horribly.

as far as the drivers:  i just recently found out that if the driver i found was built for a 64-bit, then it most certainly would not work with my OS.  i got this driver a while back and don't remember, so i feel like my next step would be to try and locate a driver that is DEFINATELY 32-bit, and definitely fits my device.  it is possible that with the commands that u gave me, we are disabling e100, and maybe even loading ndiswrapper, but that the driver I found is failing to operate correctly.  so i'll try that.  maybe u have some suggestions where i could find that driver?  the majority of hours spent on this issue has come with locating the driver...

Device:  Intel PRO/100 VE Network Connection
#: 8086:1094

thanks again

---

### Post by chili555 on 2010-04-11
These are 32-bit drivers, there might be something here that works.

---

