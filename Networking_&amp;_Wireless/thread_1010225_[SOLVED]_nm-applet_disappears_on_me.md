---
title: "[SOLVED] nm-applet disappears on me"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by rafe101 on 2008-12-13
It does this quite frequently to me—usually happens while trying to connect, or right after connection.  Often, running it again doesn't bring it back, and if it didn't finish connecting, I have to restart in those cases.

Another issue I have with it is it very often doesn't display the wireless network at all.  I'll type the name in manually and then it will connect and display the network.

Any ideas for either?

---

### Post by The Cog on 2008-12-13
Try installing wicd instead - you can always reinstall network manager if you don't like wicd.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by rafe101 on 2008-12-13
Thanks, it looks like a good alternative.

---

### Post by The Cog on 2008-12-14
I would be interested to know how you get on with it.

---

### Post by leffect on 2008-12-23
I used WICD with Hardy until recently because I wanted the computer to connect on boot and have different DNS servers for different connections, but the main reason I moved to Intrepid was for the improved Network Manager, which works perfectly with my HSDPA dongle. It also works fine when I'm at home, connects to my wireless network with no issues at all, but when I'm at work nm-applet loads, spins the green balls for a couple of minutes then segfaults.

The IT monkeys here have just switched from normal WPA to I think LEAP which authenticates with our domain username and password. Is there likely to be a link there? I was able to connect with WICD (although it took some setting up!) but Intrepid's network manager doesn't like it.

---

