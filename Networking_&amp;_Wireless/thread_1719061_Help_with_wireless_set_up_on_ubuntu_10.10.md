---
title: "Help with wireless set up on ubuntu 10.10"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by bookabooka on 2011-04-01
Hi

I am very new to Linux and am having some issues with this heap of junk home theater pc that was once riddled with over 9k of virus' lol.

I installed Ubuntu on here as its better than windows in my eyes and wanted to only have a small pc at home but troubles began soon after...

My last and unresolved issue is with the wireless. I can see the wireless network, attempt to connect to it, enter password, then enter password etc etc etc it will not just connect. I know the password is right as I set it up its a WPA/WPA2 security.

I keep looking at lspci -nn and for the life of me I cannot see wireless. I know the unit under windows has a Ralink Internal wireless adapter but any more info than that I dont know as I dont know where to look for this info.

Please help me.

I shall post the output of lspci -nn


00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:05.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
01:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 02)
01:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]

Does this make sense to anyone???

Thanks

---

### Post by MrEgg on 2011-04-01
Can you post the result of
```
sudo lshw -C network
```

---

### Post by bookabooka on 2011-04-01
Hello

Thanks for the reply here is the output


 *-network               
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:64:ea:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=192.168.2.3 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:febfe000-febfefff ioport:ec00(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:19:db:92:3e:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-28-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by MrEgg on 2011-04-01
Is this a usb wireless dongle? 

Please post the result of
```
lsusb
```

Also, connect to the internet (I suppose the wired connection works okay), and click : 'System - Administration - Restricted Drivers' and see if there's any update available for your wireless nic.

---

### Post by bookabooka on 2011-04-01
Hi

The wireless is integrated with the motherboard and I dont have an USB adapter. The web works fine wired as that is how I have to connect :(

When I went to System>Administration I only have the option for Additional Drivers which I have looked in but it finds nothing.

It seems weird that it will find the network but wont connect, my android phone will, 4 other laptops (windows pah) will and 2 Desktops can, its not out of range and I have power cycled the router... 

Im confuzzled.

Anyway here is the output

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0102 Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MrEgg on 2011-04-01
Additional Drivers was what I meant, indeed - so you have searched the right place.

I think the problem comes from driver that's being used for your wireless -- there's most likely nothing wrong with your router.

Apparently, you'd being using 
> Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573

I'll come back to you for additional tweaking / testing once I find something on that hardware.

---

### Post by bookabooka on 2011-04-01
Thank you for your help would love to get this thing running on wireless anymore info just shout. :)

Thanks

---

### Post by MrEgg on 2011-04-01
Okay, you could try :
```
sudo apt-get install firmware-ralink wireless-tools
```

Maybe reboot your system after that, just to make sure everything is loaded up properly. Then give it another go connecting to your wifi, and post :
```
iwconfig
```

---

### Post by bookabooka on 2011-04-01
Hi

Here is the output of the 2 commands respectively, I havent rebooted yet as it ame up with error.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-ralink

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by MrEgg on 2011-04-01
firmware-ralink is no longer available? I wasn't aware of that. Okay, well, maybe you could try and install the windows driver. Maybe you have it somewhere on a cd, or there's a site you can go to download it from. You're looking for an *.inf file.

```
sudo apt-get install ndisgtk
```
System - Administration - Windows Wireless Drivers (or something like that)
Click on the 'Install new driver' button.

Good luck

---

### Post by bookabooka on 2011-04-01
Hi again

I tried to download the windows driver off ralink website but the file said 1day+ remaining to download so i tried again... no luck.

But i found what I think is the right driver off their linux page and extracted this to a folder.

How do I install this driver??

Thanks

---

### Post by MrEgg on 2011-04-01
Which one did you download?

---

### Post by bookabooka on 2011-04-01
Hi

I downloaded a windows .inf for the wireless card.

Windows wireless drivers program said hardware present > rebooted > dos screen on boot up asked for some kind of login (never came up ever before) but just pressed esc and took me into ubuntu but will not show wireless at all now.

Removed the driver > rebooted, still dos screen asked for login > ignored > into ubuntu.

was going to do another fresh install but when i got to the option to erase disc i couldn't be bothered to get all my files back again so ran the live cd (via usb) > found wireless.

Shut down > rebooted > no login screen at dos > ubuntu still no evidence of wireless networks...

This is weird as I could see wireless networks before but now cannot see any. 

The linux driver i downloaded was called 2011_0210_RT73_Linux_STA_Drv1.1.0.5.bz2
from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
driver link (verson number 1.1.0.5 as this one showed rt2573....

have i broken it?? also just to be curious do you get virus' on ubuntu?

---

### Post by MrEgg on 2011-04-01
Don't worry about getting a virus on Ubuntu. The problem still lies with your not having the proper wifi driver yet.

May I suggest you should try booting up your system with a live cd of Ubuntu 10.04? I see that version has a package called rt73-common which is designed to download the firmware image needed for your wifi ([http://packages.ubuntu.com/lucid/rt73-common]("http://packages.ubuntu.com/lucid/rt73-common")). This package doesn't look present in Ubuntu 10.10.

In 10.04, if your wifi is not working out of the box, you would have to launch in Terminal
```
update-rt73-firmware
```
Keep us posted how this goes

---

### Post by bookabooka on 2011-04-01
okey dokey

What I may do is download and install 10.04 as I have read lots about how it works better with wireless and stuff.

I shall move my files to another storage device. 

Many Thanks for your help.

I will let you know if it works. :)

---

