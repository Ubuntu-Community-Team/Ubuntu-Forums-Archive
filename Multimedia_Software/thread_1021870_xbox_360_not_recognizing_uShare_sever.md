---
title: "xbox 360 not recognizing uShare sever"
date: 2008-12-26
forum: Multimedia Software
---

### Post by macaholic on 2008-12-26
Here is my issue, I am trying to use uShare to stream video from my linux computer to my xbox 360, however, the xbox cannot find my computer during its scan. I have my "/etc/ushare.conf" configured as such: ```
USHARE_NAME=ushare
USHARE_IFACE=eth2
USHARE_PORT=
USHARE_DIR=/home/matt/test/
USHARE_OVERRIDE_ICONV_ERR=

```
And eth2 IS the interface my network is on, as shown by ifconfig:```
eth2      Link encap:Ethernet  HWaddr 00:1b:63:ef:23:25  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:feef:2325/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92832468 errors:1 dropped:0 overruns:0 frame:46412447
          TX packets:112235573 errors:242 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4128671662 (4.1 GB)  TX bytes:1266694630 (1.2 GB)
          Interrupt:19 

```
as well as iwconfig: ```
eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:192  Noise level:173
          Rx invalid nwid:0  invalid crypt:74579  invalid misc:0

```
The output of "ushare -x" is as follows: ```
Interface eth2 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.2.100:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/matt/test/
Found 2 files and subdirectories.

```
Any input, ideas, or suggestions are greatly appreciated, thanks for the help.

---

### Post by ELF_O8 on 2008-12-26
Seeing as its a 360 made by that awesome company M$ it may hate your computer and drop packets on purpose because it recognizes the awesome power of the *nix

---

### Post by macaholic on 2008-12-26
> **ELF_O8 said:**
> Seeing as its a 360 made by that awesome company M$ it may hate your computer and drop packets on purpose because it recognizes the awesome power of the *nix
I doubt it, I know people have gotten this to work, so...Anyone have some advice?

---

### Post by mb_webguy on 2008-12-26
I ran into a similar issue getting my new PS3 to recognize a MediaTomb server running on my desktop.  After playing around with the MediaTomb configuration for a while I finally thought of looking at my router to make sure it supports UPnP -- which I discovered it does, but that it isn't enabled by default.  Enabling it and restarting the router and the MediaTomb server solved the problem.

---

