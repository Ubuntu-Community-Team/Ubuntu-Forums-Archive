---
title: "Help needed, no internet connection!"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by Dangerouge on 2010-06-18
Hello everyone and thanks in advance!

I'm using the latest version of Ubuntu studio, with the .22 kernel and I'm pretty new to Linux as it is today. However, my problem was this: I have a Netwjork 154mbps usb wlan stick (it's that damn W311U too, cost me 10€) and I wanted to get it to work. Before that I could still access lan on my work computer (my ubuntu is on a usb hd). So yesterday I used the resources on the internet and compiled myself a .dat and everything, except blacklisting stuff or adding to the modules, because I ran out of time. Now I'm back at work, and now also my LAN works only on the windows side, what happened? Also my network manager has managed to disappear, and when I start it, it says it's already running, I have also tried removing and adding the notification area, but to no prevail. 

Please, gurus of the bitworld help me!

Here are some tests I've tried today (please note that the W311U is not connected right now as I'm at work)

```
aranubanti@kabellah:~$ sudo NetworkManager
[sudo] password for aranubanti: 

** (NetworkManager:1845): WARNING **: NetworkManager is already running (pid 991)
aranubanti@kabellah:~$ NetworkManager
You must be root to run NetworkManager!
aranubanti@kabellah:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr e0:cb:4e:5b:20:f3  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe5b:20f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3931 (3.9 KB)  TX bytes:4061 (4.0 KB)
          Interrupt:39 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15784 (15.7 KB)  TX bytes:15784 (15.7 KB)

aranubanti@kabellah:~$ sudo ifconfig eth1 down
aranubanti@kabellah:~$ sudo ifconfig eth1 up
aranubanti@kabellah:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr e0:cb:4e:5b:20:f3  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe5b:20f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6721 (6.7 KB)  TX bytes:7138 (7.1 KB)
          Interrupt:39 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81826 (81.8 KB)  TX bytes:81826 (81.8 KB)

aranubanti@kabellah:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

aranubanti@kabellah:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03f0:0324 Hewlett-Packard 
Bus 002 Device 004: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 002 Device 003: ID 03f0:0317 Hewlett-Packard LaserJet 1200
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0d49:7110 Maxtor 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aranubanti@kabellah:~$ cat /etc/modprobe.d/blacklist.conf
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
aranubanti@kabellah:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
aranubanti@kabellah:~$ 
```

---

### Post by Dangerouge on 2010-06-18
Right... Update on doing nothing of any real use: I managed to get the Network Manager visible again, it was simple enough: $sudo killall NetworkManager , however, that's of no use, really, since it sees no connections it could use.

---

### Post by Dangerouge on 2010-06-18
OK, now I got the LAN working at the office (DNS info had been overwritten) but at home I only have WLAN, so I need to get that to work. The model is W311U and I already have installed the RTA2870 module, however whereas yesterday I had wlan0 in the iwconfig, I do no more, so network manager doesn't give me anything. Please anyone in the know of the W311U installation, help me.

---

### Post by Iowan on 2010-06-18
For what it's worth...
Just so your's isn't the only userid in the thread ;)
You seem to be making progress. The W311U is foreign to me, but **sudo lshw -C network** should provide some information. Sounds like it was working at the office...

---

### Post by Dangerouge on 2010-07-02
I got that working about a week ago, but haven't got the slightest clue how, since I tweaked so many settings and installed so many drivers, However the final mend that ultimately made it work was to install the latest RT3070STA driver. That being said, I tried doing just that on another computer to no prevail.

---

