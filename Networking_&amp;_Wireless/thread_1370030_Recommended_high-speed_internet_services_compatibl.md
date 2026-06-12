---
title: "Recommended high-speed internet services compatible with Ubuntu"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by RSASKA on 2010-01-01
Happy New Year!


I have Ubuntu 9.04 on Dell Inspiron 1545. Currently I use Verizon high-speed and use Westel Model 7500 router. Please recommend high-speed (i.e. DSL, Cable) internet services that are best suited to the Ubuntu family. I am seriously looking to get away from Verizon, but I don't want to end up with an even WORSE provider.

---

### Post by chrisamiller on 2010-01-01
Ubuntu (and all modern operating systems) are pretty much provider-agnostic. The modem the provider provides you with takes care of all the ISP-specific functions. As long as there are bits coming in the network port, Ubuntu doesn't care whether you're hooked up to cable, DSL, or a T1 on the other end.

---

### Post by Barriehie on 2010-01-01
COX is my provider and has been for many years without any issues on their end.  Zoom modem and direct connect.  Was using Motorola surfboard modems before but they start failing at about 3 years and it's a drag to troubleshoot!

---

### Post by RSASKA on 2010-01-02
Good Morning,

Thank you all for your responses.

@Barry: please clarify " Zoom modem and direct connect." Is this a special type of modem?

---

### Post by peepingtom on 2010-01-02
Hi,

As long as the ISP doesn't require you to use a special USB device, you'll be fine. If they give you a modem/router with an ethernet connection, you won't have a problem.

[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)
DHCP should automatically configure your connection, just connect your modem or whatever to your computer via ethernet (looks like a big phone cable) and your connection will work. If you go with DSL (high speed over phone lines), it might use PPPoE. Ubuntu easily supports that, you'd configure it with NetworkManager (right click on the networking icon in the notification area, aka "system tray". You'll see what I'm talking about.

Good luck, post back if you need help setting it up

---

