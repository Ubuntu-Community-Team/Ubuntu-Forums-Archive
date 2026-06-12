---
title: "Using apt-get wirelessly causes router disconnect."
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by Nakor BlueRider on 2009-03-31
The router is used, it was given to me by someone who upgraded to a better one, but seems to be in fully working order.  I'm using it with two systems, my windows desktop (which is wired directly to it) and my Ubuntu 8.04 laptop, which is connecting wirelessly.  The router is a NetGear Rangemax, and has fully updated firmware.

Whenever I try to install programs on the laptop wirelessly (whether I use apt-get, update manager, synaptic, etc.) it gets a few seconds into the download, and then the router disconnects, causing internet to be lost for both the laptop and desktop.  The only way I've found to get the internet back is to unplug the router for a second.

Now, I can do next to anything *else* with no problem.  I downloaded a 60MB file to test, and it downloaded fine (actually downloaded significantly faster than the desktop).  I am also able to connect to the laptop via SSH (from my desktop, using my modem's IP, not the router's).  It also works fine if the laptop is wired to the router, just doesn't work when it's wireless.  I've tested the problem with the router set to both WPA and WPA2, no difference.  However any attempt to apt-get something lasts no more than 3-5 seconds before the router just dies for no apparent reason.  (After this happens, I cannot access the router's IP from either computer.)

Any ideas as to possibly make this work, or what might even cause it?  Half the reason I wanted a router is so that I wouldn't have to wire my laptop in every time I wanted to run updates.

---

