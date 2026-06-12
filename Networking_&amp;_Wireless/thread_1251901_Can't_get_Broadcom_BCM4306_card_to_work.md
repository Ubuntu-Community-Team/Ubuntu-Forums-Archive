---
title: "Can't get Broadcom BCM4306 card to work"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by hathiphnath on 2009-08-28
Hi all!

I've tried to use multiple guides on the net (except some very old ones I thought might be dated at this point). At this point, I have a bunch of drivers blacklisted and an unworking ndiswrapper in use. I'm not sure how to undo those steps.

**NB!** The PC setup is different from what I have in my signature! The 250-character cap just didn't let me add them both! :(

**SETUP:** Canyon P4X400 mobo; Pentium4 (2.66GHz, 32-bit); nVidia GeForce 6600GT (128MB); 1GB DDR RAM; Broadcom BCM4306 802.11b/g wireless
32-bit Ubuntu 9.04 Jaunty Jackalope

Maybe this will tell someone here more than it tells me:

> [COLOR="Red"]~$ lspci -nn[/COLOR]
00:00.0 Host bridge [0600]: VIA Technologies, Inc. P4X333/P4X400/PT800 AGP Bridge [1106:3168] (rev 03)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:0d.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
00:0d.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:00f1] (rev a2)
[COLOR="red"]~$ lsusb[/COLOR]
Bus 001 Device 003: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="red"]~$ lshw -C Network[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:50:22:90:b3:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:4a:43:71:fd:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[COLOR="red"]~$ uname -rm[/COLOR]
2.6.28-11-generic i686
[COLOR="red"]~$ iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Any help? :)

---

### Post by jquill on 2009-08-28
I've heard that in 2008 Broadcom stopped  supporting and therefore updating Linux functionality.

---

### Post by hathiphnath on 2009-08-28
This card must be older than that... I've had it for a few years. It used to work (though with an unstable connection) on 64-bit jaunty, but I failed miserably when I trying to follow the steps I did that last time. :(

---

### Post by hoink on 2009-09-03
you and i are in the same boat, Jaunty 9.04 broadcom 4306 rev 03 seems to be giving would-be ndwiswrapper users fits.

Even when b43 is blacklisted and doesn't appear in lsmod, it's still "around":...

According to lshw -c Network, b43-pci-bridge jumps on the device 2 seconds after boot.

---

### Post by hathiphnath on 2009-09-04
Please post your solution here if yo do manage to get the card to work...

---

### Post by Ayuthia on 2009-09-04
Does anything show up in dmesg:
```
dmesg|grep b43
```

---

### Post by grammyonthego on 2009-09-10
I have the same Broadcom card and had a miserable time trying to find out how to activate it. Here is what I did:
Connect to my Router using an Ethernet cable.

Download all the latest stuff using Applications>Add/Remove.

Download and install all the latest updates using System>Admin>Update Manager.

Go to System>Admin>Hardware Drivers and activate the Broadcom B43 wireless Driver.

Unplug the Ethernet cable from the computer. (I think this is key, because the Ethernet connection auto-disables wireless.)

Clicked on the Wireless icon (top right) and selected my wireless' Radio Button. (The name had magically appeared!)

Entered my WEP  Encryption key just like I did on Windows.

I'm not sure the first two steps are necessary, but who cares....

Good Luck.

---

### Post by kerry_s on 2009-09-10
> Please post your solution here if yo do manage to get the card to work...

connect to the internet
sudo apt-get install b43-fwcutter
reboot

it's that simple! i keep the firmware on usb now so i can just copy them over with out fetching the ethernet.

copy /lib/firmware/b43 & /lib/firmware/b43legacy

---

### Post by Lori700698 on 2009-10-04
> **kerry_s said:**
> connect to the internet
sudo apt-get install b43-fwcutter
reboot

it's that simple! 

You just saved me hours....THANK YOU!!!!

---

### Post by jstrowe on 2009-10-06
> **kerry_s said:**
> connect to the internet
sudo apt-get install b43-fwcutter
reboot

it's that simple! i keep the firmware on usb now so i can just copy them over with out fetching the ethernet.

copy /lib/firmware/b43 & /lib/firmware/b43legacy

When I try to use "sudo apt-get install b43-fwcutter" it always times out when trying to access  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2). I can get this file by using another computer and putting it on a flash drive. How can I install b43-fwcutter from a file and not from the web?

Thanks,
John

---

