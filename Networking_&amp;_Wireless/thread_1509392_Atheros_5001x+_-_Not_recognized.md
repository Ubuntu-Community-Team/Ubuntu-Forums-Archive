---
title: "Atheros 5001x+ - Not recognized"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2010-06-14
Hello Everyone,

I know there are a lot of threads about this particular wireless chip, but my problem is a little different.

I have introduced Ubuntu to a firend who wants it installed to his laptop (Celeron M 1.4Ghz, 1Gb mem, Via/S3 graphics).  As always, I tried the live CD to assess hardware, and graphics has issue, but I am sure I can fix that.  But, the internal Atheros 5001x+ wireless is not even recognized by the system.  All of the other threads I have seen about this chipset are about connection difficulties.  This is only recognized by lspci (correctly) on pci bus 006.  However, because it is an Atheros the ath5k module is loaded automatically, but network manager does not even see it exists.

I tried older distros with some proprietory modules (i.e. PCLinux 2009) and it works.  lsmod shows that in these older distros the ath_pci and ath_hal modules are being loaded.  I believe these are the modules used by madwifi, which I am not even sure is being used any more.  Almost any other USB wireless stick works (tried two).  If I can get the system to acknowledge the existence of the internal wireless, I believe I can fix it.

Anyone have any ideas about a starting point?

---

