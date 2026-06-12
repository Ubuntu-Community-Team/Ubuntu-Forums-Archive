---
title: "Error: phy0: tx overflow and sometimes kernel panic"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by rbrauns on 2009-03-03
I'm a new user of Linux and have only had Ubuntu Interpid for about a week.  I like it but my system used to hang with a kernel panic but after installing some PGP keys, I've been able to update properly.

Now my system just hangs. What happens is that I loose the connection to the internet.  The message then appears, saying trying to reconnect but then the only way for me to get my WLAN working again is a restart.

The system log shows dozens of errors with phy0: tx overflow.

lspci reveals: Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

How to fix this?

---

### Post by dorpm on 2009-05-04
The reason might be the same as decribed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363528](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363528)

Regards,
Florian

---

