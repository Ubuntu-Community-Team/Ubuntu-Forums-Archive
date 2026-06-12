---
title: "Modem host pipe sharing with socat?"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by dsjstc on 2011-03-15
I'm trying to share two modems between four (VirtualBox) processes.    The problem is that each Virtualbox process insists on having a dedicated host device at startup, and can't change the device at runtime.

Someone suggested that I set the Virtualboxen to use a host pipe for their serial port, and redirect the physical port to that host pipe with socat.  It basically works, I've been able to issue AT commands to the modems and see responses, but it doesn't work when I try to actually use them as modems.

The Virtualbox forum thread is here:
[http://forums.virtualbox.org/viewtopic.php?f=7&t=39762](http://forums.virtualbox.org/viewtopic.php?f=7&t=39762)

Any advice much appreciated.

---

