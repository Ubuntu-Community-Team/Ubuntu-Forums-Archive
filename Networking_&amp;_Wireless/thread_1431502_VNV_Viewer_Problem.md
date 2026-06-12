---
title: "VNV Viewer Problem"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by Charlie Tame on 2010-03-16
Despite some time searching I don;t see anyone commenting on this problem so here goes. Updated home and work machines to 9.10 and have not used VNC for a while but last week I set up the Gnome server at home and tried it out from work using the "Remote Desktop Viewer that's in the Internet menu.

When I first connect I see my home screen and appear to have control but at work the screen never updates. Now I know the home machine is getting the commands and clicks etc because if I close the connection and the reconnect it has done what I asked it to do, I just don't see any change at this end.

Anybody think of anything obvious that could be wrong here?

I will say our IT use Squid Proxy, but I had no problem before but I don't (Yet) know if they have recently changed something.

---

### Post by sparky-steve on 2010-03-18
I'm suprised you couldnt find any reference to this on the forums; it is referenced many, many times....

Anyway, compiz (desktop effects) is likely to be your problem.

Go to System, Preferences, Appearances, on the Visual Effects tab, select NONE, and try again.

This is a known bug, and I've seen a few workarounds on this forum

---

### Post by Charlie Tame on 2010-03-19
Thanks, will do that, obviously I was using the wrong search terms :)

---

