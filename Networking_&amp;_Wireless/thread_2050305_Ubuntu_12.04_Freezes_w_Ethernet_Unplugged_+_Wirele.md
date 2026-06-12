---
title: "Ubuntu 12.04 Freezes w/ Ethernet Unplugged + Wireless Drops (Acer Aspire 5516)"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by lilmalice on 2012-08-30
Ubuntu 12.04-12.10 32/64 freezes or won't boot if the Ethernet cable is unplugged and will not hold a wireless connection.

Here is my scenario...

Laptop: Acer Aspire 5516
Wireless card: Broadcom BCM4312

**_Ubuntu 12.04 32/64 Issues_**
[LIST=1]
[*]Unity 3d **won't** load without the Ethernet cable plugged in. If I let it load with Ethernet plugged in, it will freeze once I disconnect the cable.
[*]Unity 2d **will** load without the Ethernet cable plugged.
[*]In Unity 2d, wireless cannot hold a connection. I can connect to a Wireless network, but when I try to use it (i.e. open a browser), it disconnects. I can reconnect by disabling wireless (uncheck Enable Wireless), re-enable wireless, and reconnect. But, it will disconnect again once I start using it. 
[/LIST]

**_Ubuntu 12.10 Issue_**
[LIST=1]
[*]Since 12.10 only gives me the option to load 3d (I assume), I experience the same thing as the first issue in 12.04.
[/LIST]

**_Attempted Solutions_**
[LIST=1]
[*]Enable networking/LAN in BIOS
[*]Set LAN first in boot priority in BIOS
[*]Remove STA wireless driver (bcmwl-kernel-source) and install b43 low power driver (firmware-b43-lpphy-installer).
[*]Remove default Network Manager and install Wicd.
[/LIST]

So far, I have had no luck with fixing this issue. 

Does anyone have any further suggestions?

---

### Post by Zoltair on 2013-02-08
I've got the same/similar problem with another Acer Aspire laptop. Although I can disable the wired connection and the wireless appears to function just fine, but unless the ethernet cable is plugged in the OS will freeze, mouse still functions, but can only move the mouse around the desktop, it does not respond to anything else but an abrupt and physical power down. Using 12.10 desktop as the OS of choice. If I leave the Ethernet cable plugged in, everything works great, but once I unplug it, the little windows stating no wired connection pops up and never goes away. Any suggestions would be great, even some way to get diagnostic data might help.

Without further suggestions my only option would be to return back to a Microsoft environment.

---

