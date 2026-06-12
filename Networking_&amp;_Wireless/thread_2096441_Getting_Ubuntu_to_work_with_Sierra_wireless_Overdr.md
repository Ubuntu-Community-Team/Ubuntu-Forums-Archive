---
title: "Getting Ubuntu to work with Sierra wireless Overdrive Pro 3G/4G USB"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by bbabu84 on 2012-12-19
I bought a 3G/4G hotspot from Virgin Mobile, called Overdrive Pro.  It works on the Sprint network.  When the device was plugged into the computer's USB slot, the computer would freeze most of the times.  The frustrating part was that it would work some of the times, but most often, the computer freezes when the keyboard is used.  Without using the keyboard, you can continue to use the computer using just the mouse!  The computer freezes if the keyboard is used or if you reboot the system.  Searching for useful information on the web was frustrating (hence this post).  I was getting close to guessing the problem, when I found the following page:
[http://archimedesnewton.com/2012/12/04/sierra-wireless-overdrive-pro-3g4g-mobile-hotspot-802s-with-linuxmint-13-maya/](http://archimedesnewton.com/2012/12/04/sierra-wireless-overdrive-pro-3g4g-mobile-hotspot-802s-with-linuxmint-13-maya/)
The page shows what the work around is.  You need to blacklist the sierra driver to get the device to work propoerly with linux.  The following solution makes the device work for me every time:

1. Edit the file /etc/modprobe.d/blacklist.conf (say with the command "sudo vi /etc/modprobe.d/blacklist.conf") and add the line
blacklist sierra
at the bottom of the file.
2. Reboot the system.

From them on, you should be able to plug in Overdrive Pro into USB and have the system recognize the device as a network connection.  I have tested it on Ubuntu 12.10 and 12.04.

I hope this page helps other users to solve the problem without struggling with it like I did.  Now, if someone knows how to make this device have a decent upload speed!

Good luck,
bbabu

---

