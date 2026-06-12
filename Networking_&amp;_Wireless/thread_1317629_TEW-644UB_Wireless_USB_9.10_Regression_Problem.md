---
title: "TEW-644UB Wireless USB 9.10 Regression Problem"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Aurawin on 2009-11-06
Ubuntu 9.04 32bit - my TEW-644UB worked flawlessly.  With 9.10 I cannot connect to any access points.  The driver initializes and can even display access points but cannot connect to any of them.

Anyone found a work-a-round?  Thanks.

---

### Post by jbreiden on 2009-12-13
Yes, blacklisting the rt2800usb module worked for me on Ubuntu 9.10, AMD64 architecture. The kernel fell back to the rt2870sta module. [See discussion]("http://ubuntuforums.org/showthread.php?t=1256810")

---

