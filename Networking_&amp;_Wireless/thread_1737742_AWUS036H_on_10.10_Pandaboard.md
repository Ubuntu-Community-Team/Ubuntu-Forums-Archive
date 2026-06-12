---
title: "AWUS036H on 10.10 Pandaboard"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by willdex on 2011-04-23
Gentlemen, I'm really sorry that it's been over two years since I visited these forums. I'm at a total loss here. I apologize in advance if this is a long read, but I wanted to capture as much as I could, to avoid providing too little information.

I've got my Pandaboard (5A002A1), with a thought that it could serve as my 24/7 torrent-box desktop replacement. I still have faith that it's possible, but apparently need to do a lot of tweaking. I've got the board running on a 4GB Class 2 SD card with 10.10 Maverick, powered by a USB J18 port (I just couldn't find a matching 5V adapter). I've read in the manual that powering like this would be a bit restrictive, but I don't remember it mentioned anything about WiFi not working. If that's the case, I better find that adapter, fast. My both keyboard and mouse are connected via a 7-port hub with its own external supply. I don't know much about electricity, but after a few reboots shortly after both devices were used (without the hub power supply), it got me thinking that the J18 may not be supplying the two devices with enough current, so I provided the hub with its own connector - so far so good. Although the long boot isn't the question here, it takes extremely long time for the board to boot - 15 to 20 minutes, with 10 definitely being a minimum.

Anyway, I have two WiFi cards: an Alfa AWUS036H and a TP-Link TL-WN722N. These are not connected at once. I'd prefer to use the Alfa, as this is what I've been using for the past number of months on my XP tower. My Ethernet works fine, as this is how I'm posting this message. 

My essentials are all up to date, or so it seems:

> pb@pb:~$ sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Kernel:

> pb@pb:~$ uname -r
2.6.35-903-omap4

USB Devices:

> pb@pb:~$ lsusb
Bus 001 Device 011: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 008: ID 046d:c063 Logitech, Inc. 
Bus 001 Device 007: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 001 Device 006: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 004: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. 
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Network manager labels Ethernet as usb0 instead of the usual eth0 (usual to me anyway):

> pb@pb:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9120 (9.1 KB)  TX bytes:9120 (9.1 KB)

usb0      Link encap:Ethernet  HWaddr 92:54:2d:83:68:3e  
          inet addr:192.168.1.94  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9054:2dff:fe83:683e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:129110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176453381 (176.4 MB)  TX bytes:6361589 (6.3 MB)

While on **$ifconfig**, when running **$sudo ifconfig wlan0 down** and then **up**, the board reboots.

> pb@pb:~$ iwconfig 
lo        no wireless extensions.

usb0      no wireless extensions.

> pb@pb:~$ wlan0setup
wlan0setup: command not found

This method ([http://ubuntuforums.org/showthread.php?t=1605285](http://ubuntuforums.org/showthread.php?t=1605285)) didn't work due to the following error message when running make:

> pb@pb:~/Downloads/Linux driver for kernel 2.6.X/rtl8187_linux_26.1025.0328.2007$ sudo ./makedrv 
[sudo] password for pb: 
ieee80211/
ieee80211/license
....
rtl8187/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/pb/Downloads/Linux driver for kernel 2.6.X/rtl8187_linux_26.1025.0328.2007/ieee80211/tmp
make -C /lib/modules/2.6.35-903-omap4/build M=/home/pb/Downloads/Linux driver for kernel 2.6.X/rtl8187_linux_26.1025.0328.2007/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-903-omap4'
make[1]: *** No rule to make target `driver'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-903-omap4'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/pb/Downloads/Linux driver for kernel 2.6.X/rtl8187_linux_26.1025.0328.2007/rtl8187/tmp
make -C /lib/modules/2.6.35-903-omap4/build M=/home/pb/Downloads/Linux driver for kernel 2.6.X/rtl8187_linux_26.1025.0328.2007/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-903-omap4'
make[1]: *** No rule to make target `driver'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-903-omap4'
make: *** [modules] Error 2

But then I read somewhere that the RTL8187  driver isn't that good for surfing the net, but only for penetration testing. So I guess, this one is out. Also, because it's Pandaboard (ARM architecture), I think ndiswrapper won't work.

The rc.local file:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

I then looked into simply downloading drivers for my other WiFi card, TP-Link TL-WN722N: [http://webcache.googleusercontent.com/search?q=cache:cK-iqRG-PBcJ:www.omappedia.org/wiki/PandaBoard_FAQ+pandaboard+wifi+driver&cd=3&hl=en&ct=clnk&gl=us&client=ubuntu&source=www.google.com](http://webcache.googleusercontent.com/search?q=cache:cK-iqRG-PBcJ:www.omappedia.org/wiki/PandaBoard_FAQ+pandaboard+wifi+driver&cd=3&hl=en&ct=clnk&gl=us&client=ubuntu&source=www.google.com). The reason I give a google address is because [www.omappedia.org](www.omappedia.org) is down at the moment (it's been down for a day or so). 
This time it's too many packages to look through ([https://launchpad.net/~tiomap-dev/+archive/release/+packages](https://launchpad.net/~tiomap-dev/+archive/release/+packages)), but I got the "ubuntu-omap4-extras-connectivity_0.1.tar.gz", but it doesn't contain anything that I can actually install.

I've read through several sites and advices on various forums (even [Aircrack forum]("http://forum.aircrack-ng.org/index.php?topic=5755.0") didn't help). However, none describe the setup I have. I'd appreciate any assistance, no matter how little or vague.

--Thanks for your help, Will.

---

### Post by willdex on 2011-04-24
Additional info, blacklist file. I first thought of removing comments to save some space, but then decided to keep the integrity of the file:

> # This file lists those modules which we don't want to be loaded by
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

If possible, please provide feedback. If necessary, I am willing to redo everything from scratch.

---

