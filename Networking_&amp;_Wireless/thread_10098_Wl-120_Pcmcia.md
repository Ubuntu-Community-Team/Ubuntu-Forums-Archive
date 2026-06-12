---
title: "Wl-120 Pcmcia"
date: 2005-01-04
forum: Networking &amp; Wireless
---

### Post by telmo on 2005-01-04
After i installed the Windows driver for Ndiswrapper (wlanCIG.inf) i rebooted and the computer recognized a Prism card, wich doesn't work, instead of mine.

Any solutions ?

---

### Post by telmo on 2005-01-04
SOLVED IT!
Just deleted all files containing prism54 and removed the module (modprobe -r prism54) :D

That was fast!

---

