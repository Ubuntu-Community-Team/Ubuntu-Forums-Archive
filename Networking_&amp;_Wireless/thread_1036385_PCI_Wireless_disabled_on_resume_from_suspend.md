---
title: "PCI Wireless disabled on resume from suspend"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by fprintf on 2009-01-10
[Solved]I have an IBM T30 laptop with a TrendNet TEW-441PC wireless PCI card. The wireless card, only 3 days old for me, works fantastically and was $10 from Buy.com. Can't beat that!

The card works great when I boot the computer from shutdown. The card connects to my network immediately and flawlessly and does so thru the standard kernel modules - I didn't need to compile, manually modprobe or do anything. I just worked after I plugged it in and rebooted. The problem, somewhat similar to comments I have read earlier is that the card is not recognized upon a resume from standby. I am using Network Manager 0.7.0, and as I said whatever standard drivers are in place.

I have already tried adding "networking" to my resume from suspend section in /etc/default/acpi-support. I had read that I should consider adding my kernel module into acpi-support. How do I figure out what module is being loaded?  Is there any alternative?

---

### Post by fprintf on 2009-01-11
I did some checking of /var/log/messages and thought I would post the output here in case some helpful soul can figure out what is going on. I can get wireless running only by unplugging the PCI card and pushing it back in the slot.

I have added comments illustrating the various timepoints by using '>> --- Comment' in the /var/log/messages file I included at [http://pastebin.com/d5f3fe2ec](http://pastebin.com/d5f3fe2ec)

---

### Post by fprintf on 2009-01-11
[http://ubuntuforums.org/showpost.php?p=4914094&postcount=32](http://ubuntuforums.org/showpost.php?p=4914094&postcount=32) had the solution.  The answer is to modprobe -r ath-pci and then reinsert it upon resume. The trick is to ensure the 49filename file is executable, something I didn't realize until I read [http://wiki.archlinux.org/index.php/Pm-utils](http://wiki.archlinux.org/index.php/Pm-utils)

---

