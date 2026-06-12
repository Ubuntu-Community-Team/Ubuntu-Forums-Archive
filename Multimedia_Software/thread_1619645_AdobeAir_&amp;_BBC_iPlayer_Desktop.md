---
title: "AdobeAir &amp; BBC iPlayer Desktop"
date: 2010-11-12
forum: Multimedia Software
---

### Post by Krister Hallergard on 2010-11-12
Installing on 10.10 64-bit works fine following the instructions on [http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html).  The BBC Desktop functions well once I reenabled KWallet.

My problem is that when I refresh the repositories the BBC Desktop is reported as broken, and the reason seems to be that AdobeAir does not show as installed in Synaptic.  It does not matter if I install AdobeAir using .deb or .bin, it still is not reported as installed.  Any ideas about how to make AdobeAir show as installed?

---

### Post by Krister Hallergard on 2010-11-15
The solution was simple once I thought of it:  Install the BBC Desktop, copy its folder somewhere, uninstall the BBC Desktop and copy the folder back to its previous position.  Both AdobeAir and the BBC Desktop work, and neither of them show up as installed in the database, so there is no broken message.

---

