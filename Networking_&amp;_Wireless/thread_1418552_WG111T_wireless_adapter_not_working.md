---
title: "WG111T wireless adapter not working"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by Gamemaster1379 on 2010-02-28
I have been searching for days on end trying to get my machine to detect my Netgear WG111T wireless adapter...and I've gotten absolutely nowhere at all. 

Most tutorials suggest I use ndigstk(sp?), which allows me to use Windows drivers for my adapter. I've been told many times to use the wg111t.inf file, but all I've been able to come up with is the w11t.inf file. Whenever I start up the Windows Wireless Drivers application, I usually get a popup which tells me "Unable to see if Hardware is detected"--yet when I hit the OK prompt, next to the w11t.inf file, it says "Hardware detected --Yes", yet I still have gotten nowhere. I grasp some basics of Linux, but overall I'm still pretty new to it--and I have a big headache from the whole thing. :?


EDIT: I forgot to mention, my install is 9.04, so if 9.10 resolves this, how would I go about upgrading without downloading an ENTIRELY new disc (I have a horrid internet connection, it'd take HOURS to download the 699MB ISO, so perhaps make that a last resort)

---

### Post by chili555 on 2010-02-28
Isn't this an Atheros-based card? Let's see with a terminal command:```
lspcmcia -v
```Thanks.

---

### Post by Gamemaster1379 on 2010-02-28
> **chili555 said:**
> Isn't this an Atheros-based card? Let's see with a terminal command:```
lspcmcia -v
```Thanks.
I tried the command and well....nothing happened as far as I could tell. I didn't see any noticable changes, and terminal did nothing in reply. It simply brought up the next command entry line X@ubuntu$.

---

### Post by chili555 on 2010-02-28
OK, I wiped off these old glasses and I see it's a USB device. Sorry. May I please see (no pun intended!):```
lsusb
```Thanks.

---

### Post by Gamemaster1379 on 2010-02-28
Not a problem.

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0810:0001 Personal Communication Systems, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 006 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-02-28
I see a keyboard, a USB harddrive, a bluetooth device and a (maybe) joystick; but nothing like a USB wireless device. Is it plugged in? Is it defective?

---

### Post by Gamemaster1379 on 2010-02-28
It's definitely working, that's how I'm online now. As far as it being plugged in, it may not have been the first time, I don't know, but here's the results again, it shows up in these.

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 1385:4250 Netgear, Inc WG111T
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0810:0001 Personal Communication Systems, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 006 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-03-01
I have read several posts that suggest you need to install two drivers. Here, for example: [http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/](http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/)

> *sudo ndiswrapper -i netwg11t.inf* # Install the Wi-Fi Driver

At this point I tried plugging in the dongle but its blue light didn’t begin flashing.

*sudo ndiswrapper -i athfmwdl.inf* # Install the Boot-Loader Driver

After this I plugged the dongle in again and the blue light started to flash.

It appears that the bootloader piece is what you might be missing. I suggest you try this method.

---

### Post by Gamemaster1379 on 2010-03-01
> **chili555 said:**
> I have read several posts that suggest you need to install two drivers. Here, for example: [http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/](http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/)



It appears that the bootloader piece is what you might be missing. I suggest you try this method.
Hate to say this, but this didn't work either. Windows Network Manager still gives me the error that it's unable to see if hardware is plugged in. What a nuisance :<

Also, it's a crazy suggestion, but if I were to install Windows inside of Linux and seamlessly run them...Would it be possible for Windows to bridge the connection from the WG111T to Linux, so both would run it? I have an XP copy I could use, and my system is perfectly capable of running both simultaneously.

---

### Post by chili555 on 2010-03-01
> Also, it's a crazy suggestion, but if I were to install Windows inside of Linux and seamlessly run them...Would it be possible for Windows to bridge the connection from the WG111T to Linux, so both would run it? I have an XP copy I could use, and my system is perfectly capable of running both simultaneously.Not that I am aware of; I have never heard of it. You might, however, install XP and grab the two .inf files and try those in ndiswrapper. Frankly, I am out of suggestions.

---

### Post by Gamemaster1379 on 2010-03-01
> **chili555 said:**
> Not that I am aware of; I have never heard of it. You might, however, install XP and grab the two .inf files and try those in ndiswrapper. Frankly, I am out of suggestions.
Crap, well anyway, thank you for your assistance. :D

---

### Post by Gamemaster1379 on 2010-03-01
After having been frustrated with all the errors coming up, I simply reinstalled Linux (I didn't lose anything, so no biggy there), and after having done that, I went through the steps again...and I'm almost there. Right now my network manager is showing my wireless connection name and I can select it....but after I do, it'll try to connect for sometime and just...disconnect. What am I missing here? I've heard some mention I need router drivers? Perhaps it's something I've overlooked? My router is a Linksys WRT54GL

---

### Post by PCNetSpec on 2011-03-30
I know it's an old post, but for future readers..

Don't use ndiswrapper, there are Linux native drivers for the Netgear WG111T.

Instructions here:
[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572)

---

