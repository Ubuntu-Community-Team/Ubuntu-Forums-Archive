---
title: "Ubuntu 9.04 getting IP assigned from wireless router but can't ping router"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by utvolfan67 on 2009-11-23
I am new to Ubuntu.  I installed 9.04 on my PC today & I connect to the internet via a USB Belkin adapter to Linksys wireless G router.  It sees the Belkin & I am able to configure my wireless LAN using WPA.  It assigns an IP to the Ubuntu PC but I can't ping the router or the XP machine that is connected via ethernet to the router.  ifconfig -a shows wlan0 as UP and having the IP assigned by Linksys.  Please help out a newbie Ubuntu user.  I am tired of spyware & viruses!

---

### Post by Bon Dup on 2009-11-23
i am having much the same problem with my belkin usb.
shows the available networks, but can never connect to any.

are you using a 54g?

i found afew answers when i googled "belkin 54g+ubuntu+drivers"

sorry i cant help

---

### Post by utvolfan67 on 2009-11-23
Bon Dup,
 
I am using 54g.  I can connect to the wireless network, I just can't ping the router or get on the internet.  It is really confusing since the router has assigned me an IP address.  I was wondering if there is some sort of firewall that Ubuntu has that I don't know about.  Thanks for the google tip.

---

### Post by Iowan on 2009-11-23
What IP address does it get (post **ifconfig -a**)? Hopefully not 169.254.X.X - that'd be **avahi** trying to "help".

---

### Post by utvolfan67 on 2009-11-23
> **Iowan said:**
> What IP address does it get (post **ifconfig -a**)? Hopefully not 169.254.X.X - that'd be **avahi** trying to "help".
Iowan,
 
No. I'm getting a legitimate 192.168.1.101 from the router.  Is there some default firewall settings or something like that?  I'm baffled as how the router can assign my PC an IP but I can't ping the router.  Please help....anyone.

---

### Post by utvolfan67 on 2009-11-26
I've got more info on this now.  It seems that a fairly weak signal is causing my problem.  I was getting around 40-50% signal strength where the computer was.  I decided to move it downstairs next to my router (86% strength) and now I can ping the router & get on the internet.  Of course, that's not where I need this computer.  I verified that Ubuntu is using a default driver for my Belkin adapter so I'm wondering if using a driver specific for Belkin would help with that.  Thoughts anyone?

---

