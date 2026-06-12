---
title: "Kernel Upgrade Wireless Woes"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Nrbelex on 2008-12-29
Hi, I recently upgraded from 8.04 to 8.10. Previously I had struggled to get my USB wireless adapter (Linksys WUSB11 v 2.6) working using the network manager, but switching to wicd seemed to fix my problems. Unfortunately the upgrade to 8.10 seems to have brought some of those problems back, even with wicd. 

When booting up, the progress bar under the Ubuntu logo gets almost to the very end, then freezes and displays text. The last line says "Starting Hardware abstraction layer hald". The computer never progresses beyond that point.

However, upon booting, if I select kernel 2.6.24-22 instead of 2.6.27-9, I am able to boot without a problem. If I unplug the USB adapter I can boot using the newer kernel, so I'm fairly confident the adapter is responsible for the problem.

Even if I do manage to fully boot using the old kernel, wicd rarely connects to my network. It is always able to show the signal strength, but it almost always freezes at "obtaining IP address". I do nothing different those few times it successfully connects.

Thoughts and advice are greatly appreciated!

~ Brett

---

### Post by Nrbelex on 2008-12-30
... bump.

---

### Post by Nrbelex on 2009-01-01
... any ideas...

... bump...

---

### Post by MarcoPau on 2009-01-19
I got the same problem with HALD and the only thing I can do is uninstall wicd and everything will work smoothly. Kinda sucks cause I have to manually bring up the wlan interface each boot.

If anybody has a hint...
Ciao

---

