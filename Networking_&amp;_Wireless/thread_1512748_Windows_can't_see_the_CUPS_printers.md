---
title: "Windows can't see the CUPS printers"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by rlopes528 on 2010-06-18
I recently had to reinstall Ubuntu (due to a crash after an update) and I'm having trouble to configure the print server.

The last time all I had to do was to follow this:

- System;
- Printing;
- Server;
- Settings;
- Publish printers connected to this system;
- OK.

Then I would go to the Windows box and add the printer like this:

[http://192.168.0.88:631/printers/Officejet-J4660-series](http://192.168.0.88:631/printers/Officejet-J4660-series)

And it would work perfectly.

Now I've been tweaking everything I can imagine and no luck. Any ideas?

---

### Post by rlopes528 on 2010-06-23
bump

---

### Post by mark bower on 2010-06-23
your sequence does not look the same as mine in 9.10. the below comes from my setup notes.  the key was selecting the network printer option. my computer pci card goes to my router to which the P/S is connected, and the P/S is connected to the HP4 at the parallel port.

Sys>Admin>Printing>New> Network Printer
see:
	PS-DF6EC4-P1 (PS-DF6EC4-P1)
	Find Network Printer
	AppSocket/HP JetDirect
	Internet Printing Protocol (ipp)
	LPD/LPR Host or Printer
select PS-DF6EC4-P1 (this is my print server)

mark

---

