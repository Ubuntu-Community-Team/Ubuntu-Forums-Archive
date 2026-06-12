---
title: "Wireless printer access from xp broken"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by KieranFitzgerald on 2012-12-20
I have my wireless Canon MP560 printer working with my Ubuntu (12.04) machine, this included setting an IP address on the printer.
My other machine running XP can not find the printer any more.

Any ideas as to how to fix it?

---

### Post by ahallubuntu on 2012-12-20
Are you sure the IP address hasn't changed?  This can happen for a variety of reasons (for example, resetting your router, getting a new router, etc.)  Usually, the router assigns the IP to the printer.

If the IP has changed, you could simply delete and re-install the printer in XP.  A quick-and-dirty way I sometimes use in XP is to find the port for the print driver and change the IP address there.    Like this for example:

[http://support.uidaho.edu/2011/05/20/windows-xp-changing-a-port-on-tcpip-printing/](http://support.uidaho.edu/2011/05/20/windows-xp-changing-a-port-on-tcpip-printing/)

but click "Configure Port" instead of "Add Port" - configure the existing port that is checked and change the IP address to the new one, if the IP changed.

---

### Post by KieranFitzgerald on 2012-12-21
I'm sure it hasn't changed.  This machine is dual boot XP with the printer set up before installing Ubuntu.  This prints fine from both operating systems.  It's just the other XP machine which fails to print, I can't even install the drivers again as the installer can't find the printer.

This machine is linked to my router by wireless and the other machine is wired.  All other functions on my net appear to be working.  Even tried a couple of restores.

An XP problem I suppose, just strange that it coincided with connecting to the printer with Ubuntu.

---

### Post by KieranFitzgerald on 2012-12-21
Solved
IP setting on printer wrong(sub net mask)

---

