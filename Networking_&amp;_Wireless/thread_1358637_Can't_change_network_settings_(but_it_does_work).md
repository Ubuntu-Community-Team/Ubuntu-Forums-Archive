---
title: "Can't change network settings (but it does work)"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by mikex on 2009-12-18
I can connect to the internet, but I can't add or change the network settings now. When I open "Network Connections" I see under "Wired" one listing -

ifupdown (eth0)

The edit and delete buttons are grayed out. Also, when I try to add a new connection, it seems to let me, I click "Apply" it asks me for authentication. When I enter the valid password, it seems to take it, but the new connection is never added - I also did reboot too. The original network settings I entered oh so long ago (by now I've installed many upgrades to Ubuntu) are obviously in there somewhere, but it seems now the applet won't let me change them.

Another little applet in the upper bar of the screen has a red X on it and says this when I right click for connection information -

Error displaying connection information:

No valid active connections found!

But the computer does work on the Internet OK.

That's what I need help with - how to get the graphical applet to let me edit my network settings. I'm running the very latest Ubuntu 9.10 and have installed all the updates.

---

### Post by Iowan on 2009-12-18
Check (from a terminal) */etc/network/interfaces*. This file *should* have only two lines defining "lo". If it has a definition for eth0, that would explain why internet works, but Network Manager complains.

---

### Post by mikex on 2009-12-19
> **Iowan said:**
> Check (from a terminal) */etc/network/interfaces*. This file *should* have only two lines defining "lo". If it has a definition for eth0, that would explain why internet works, but Network Manager complains.

Great! That was exactly what was wrong. Thank you for responding to my request for help.

---

