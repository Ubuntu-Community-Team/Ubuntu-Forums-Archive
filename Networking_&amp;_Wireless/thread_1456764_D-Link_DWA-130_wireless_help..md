---
title: "D-Link DWA-130 wireless help."
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by drackor1991 on 2010-04-17
Alright basically I've been trying Ubuntu 9.10 64bit out for awhile but am still a complete idiot when it comes to it. I am trying to use the info on [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to get D-Link dwa-130 to work. I get to the part of putting the .inf in. If I put the XP inf in the whole system freezes and when I restart there is no login menu anymore. So I reinstalled and tried the 2k driver. It installs but then pops up that the hardware wasn't found. It shows up on lsusb. I just need some help on what to next. If you need any logs or info just tell the command to use because I'm new to unix <.<
Thank you :)

---

### Post by perham on 2010-04-17
> **drackor1991 said:**
> Alright basically I've been trying Ubuntu 9.10 64bit out for awhile but am still a complete idiot when it comes to it. I am trying to use the info on [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to get D-Link dwa-130 to work. I get to the part of putting the .inf in. If I put the XP inf in the whole system freezes and when I restart there is no login menu anymore. So I reinstalled and tried the 2k driver. It installs but then pops up that the hardware wasn't found. It shows up on lsusb. I just need some help on what to next. If you need any logs or info just tell the command to use because I'm new to unix <.<
Thank you :)

a lsusb output would be good, also please confirm that you're using 64-bit XP drivers and not 32-bit ones.

---

### Post by drackor1991 on 2010-04-17
Bus 001 Device 006: ID 07d1:3300 D-Link System 
Bus 001 Device 004: ID 413c:5115 Dell Computer Corp. Photo AIO Printer 926
Bus 001 Device 003: ID 154b:6545 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 046d:c225 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 002: ID 046d:c068 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I can't use the XP driver or the wireless thing crashes. Then I cant do any command in the terminal, it just hangs. Then when I restart I lose the login screen. I'm using the 2k driver which I'm betting is 32 bit. It installs fine but doesnt find my d-link.

---

### Post by perham on 2010-04-17
> **drackor1991 said:**
> Bus 001 Device 006: ID 07d1:3300 D-Link System 
Bus 001 Device 004: ID 413c:5115 Dell Computer Corp. Photo AIO Printer 926
Bus 001 Device 003: ID 154b:6545 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 046d:c225 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 002: ID 046d:c068 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I can't use the XP driver or the wireless thing crashes. Then I cant do any command in the terminal, it just hangs. Then when I restart I lose the login screen. I'm using the 2k driver which I'm betting is 32 bit. It installs fine but doesnt find my d-link.

you should get 64-bit drivers. 32-bit drivers won't work. also, take a look here:

[http://joeb454.ubuntuforums.org/showthread.php?t=1354191](http://joeb454.ubuntuforums.org/showthread.php?t=1354191)

---

### Post by drackor1991 on 2010-04-17
I looked that over. It sounds good if I could ge tthe xp 64 bit to install. Everytime I do my system gets damaged. Should I try Vista 64 bit?
Also I have the E1 version if that makes a difference.

---

### Post by perham on 2010-04-17
> **drackor1991 said:**
> I looked that over. It sounds good if I could ge tthe xp 64 bit to install. Everytime I do my system gets damaged. Should I try Vista 64 bit?
Also I have the E1 version if that makes a difference.

seems that vista won't work. I found this thread too:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1440864](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1440864)

I will look into this a bit more tomorrow. ;)

---

### Post by drackor1991 on 2010-04-17
Thank you. :)

---

### Post by drackor1991 on 2010-04-18
Anyone else?

---

### Post by ktmom on 2010-04-21
I'm in this boat also.  Exactly the same as drackor1991 is describing.

---

### Post by drackor1991 on 2010-04-22
With the XP drivers crashing the whole thing too? Honestly, I just gave up. I'm running it on a VM :/

---

