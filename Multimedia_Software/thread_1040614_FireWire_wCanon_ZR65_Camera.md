---
title: "FireWire w/Canon ZR65 Camera"
date: 2009-01-15
forum: Multimedia Software
---

### Post by RX8volution on 2009-01-15
Hi all,
  My conversion to Ubuntu is almost complete.  I've installed Kino and was ready to start moving video from my Canon ZR65 camera.  Plugged in the FireWire port, started up Kino and got a /dev/raw1394 error!  I then went to my system log (messages) and pulled this nugget:

[I]Jan 15 17:32:01 zoom kernel: [288549.548536] ieee1394: raw1394: /dev/raw1394 device initialized
Jan 15 17:32:01 zoom kernel: [288549.583785] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.[/I]

Anyone know what's wrong?  I'm on 8.10 by the way.

---

### Post by skullmunky on 2009-01-16
what was the error?

---

### Post by RX8volution on 2009-01-16
From /var/log/messages:
[I]Jan 15 17:32:01 zoom kernel: [288549.548536] ieee1394: raw1394: /dev/raw1394 device initialized
Jan 15 17:32:01 zoom kernel: [288549.583785] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.[/I]

KINO Error:
**"WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!"**

There is no indication of an error anywhere in Kino, except the error I pasted above about raw1394 not being supported... very odd.

---

### Post by RX8volution on 2009-01-16
Google solved my problem, here:

[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)

---

### Post by skullmunky on 2009-01-16
file permissions on /dev/raw1394, right?  :)

---

