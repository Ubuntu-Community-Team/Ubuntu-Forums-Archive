---
title: "Wireless S10e wireless lost after suspend"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by gerardc on 2011-07-10
Hi, I have a Lenovo S10e got the wireless working with the help of [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868) but now the problem is on suspend/hibernate. I have to reboot after I close and the reopen the lid, the wireless will not reconnect, what do I need to look for ?, message logs etc.
Thanks

---

### Post by walt.smith1960 on 2011-07-10
You could try this:
[http://ubuntuforums.org/showthread.php?t=1745769](http://ubuntuforums.org/showthread.php?t=1745769)
My adapter was a USB device so I could remove and reinsert.  The problem appears to be that the wireless is not disconnected before suspending.  It can't resume because it did not first disconnect.  At least that's how I understand it.

---

