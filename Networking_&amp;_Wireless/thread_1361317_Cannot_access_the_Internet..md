---
title: "Cannot access the Internet."
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by tebucky on 2009-12-21
All,

For some reason I cannot ping anything or access the Internet from my Ubuntu 8.10 box.  However, I can ssh to the box as well as VNC into it.

What am I missing here?  This just started within the last few days.

TIA

---

### Post by steveneddy on 2009-12-21
How did you make this thread?

Is this wireless, ethernet, PCM/CIA card?

Let us know info about your hardware and what you were doing before this happened.

Did this happen after an update? Have you installed some software?

Give us more info.

---

### Post by tebucky on 2009-12-22
Sorry for the lack of info... here is what I can share.

I'm using an Ethernet behind a linksys router.  I've been assigned an IP on my LAN (192.168.1.102) successfully.

I really haven't installed any updates or even used the box in over a week so the sudden change is alarming.  No software has been installed either.

Again, other protocols like ssh and vnc work fine remotely.

---

### Post by Iowan on 2009-12-22
> **tebucky said:**
> For some reason I cannot ping anything or access the Internet from my Ubuntu 8.10 box.
Can you ping the router? I presume it must have been able to communicate well enough to at least get an IP address. Can you ping anything by IP address? If so, check */etc/resolv.conf* for valid nameservers.

---

### Post by tebucky on 2009-12-22
I can ping the router as well as an external IP.  My resolv.conf has no nameservers in it.  Is that ok since the router has DNS servers listed?

---

### Post by tebucky on 2009-12-22
Somehow my resolv.conf file had no entries in it.  I put the nameservers in and walla it working.  Thanks to all...

---

