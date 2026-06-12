---
title: "WiFi doesn't work after quitting kismet"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by biga805 on 2009-09-13
Ok, I've read nearly all the posts, and everything on google, but still can't find a solution for this.  

So I have an Acer Aspire One 8", running Ubuntu. 

Here's my uname output:
**Linux lilj 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux**

So I've been messing around with Kismet, testing my network and all that, but when I quit kismet, my wifi stops working. I can't really tell if it's still in monitor mode or what, because ifconfig shows 'UP' and iwconfig shows normal. It just won't ping out, or access the web.

here's a snippet of my kismet.conf :

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=biga

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
**ncsource=ath5k,wlan0,ath5k**

Hereis what lspci spits out:
[B]03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

[/B]Now, with that being said, (and at risk of being flamed) anyone know how to get my wireless to turn back on without having to reboot? I would seriously appreciate any tips.

Thanks in advance!

---

### Post by tgalati4 on 2009-09-13
Isn't there a small button on the front of the palmrest?

---

### Post by biga805 on 2009-09-13
Yea, to the right... LOL I swear if that's the fix.... 

*aiming foot at rear *

So that didn't work.. Also, the problem is that wlan0 is stuck in Monitoring. I checked it after running kismet, and then after a reboot, it shows Managed.

---

### Post by slavik on 2009-09-13
after exisitng kismet, set your wlan device to managed mode ...

```

sudo iwconfig <interface name> mode managed

```

---

### Post by biga805 on 2009-09-13
Tried that. 

I get the error wlan0 busy or in use...

I've been wondering though.  Could it be because I need to switch to the madwifi driver,instead of the ath5k?

---

### Post by chili555 on 2009-09-13
Please try this:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```

---

### Post by biga805 on 2009-09-13
Same result.

What about creating a montioring device? Like wlan0mon?  I tried to do that according to the kismet readme, but then kismet wouldn't work at all.  I assumed due to the fact that wlan0mon doesn't exist.  How would you create that?

---

### Post by tgalati4 on 2009-09-13
On some cards, when you put it in monitor mode, you HAVE to reboot to get it to reset. Simply turning wireless on/off with the button won't work.  Ifup/down won't work, etc.  Monitor mode captures signals in a passive mode, but also won't respond as a normal card either.

It's a pain.

---

