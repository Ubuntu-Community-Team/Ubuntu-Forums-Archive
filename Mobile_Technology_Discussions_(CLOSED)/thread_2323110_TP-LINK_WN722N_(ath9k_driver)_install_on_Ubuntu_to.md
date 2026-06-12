---
title: "TP-LINK WN722N (ath9k driver) install on Ubuntu touch 15.04 (Nexus 10- manta)"
date: 2016-05-02
forum: Mobile Technology Discussions (CLOSED)
---

### Post by RoninISC on 2016-05-02
I've been through all the relevant threads on AskUbuntu and they are either outdated, conflicting and/or dont work.

My Nexus10 sees the atheros AR9271 device on Bus 001 USB but does not  create an additional WLAN for it.(wlan0 is the normal integrated wifi).  I've done update, upgrade, and have latest build-essential. I  assume I need the ath9k or ath9k_htc driver?  I installed backports  4.4.2-1 and unzipped it. If I try to do a 'make' or 'make clean' I  get:'your kernel headers are incomplete/not installed'. If I try to install  'firmware-atheros', it cannot find the package. I've been through  several other things to no avail. 

I've read the driver is installed with 15.x+ anyway, true?  and if so  how to enable/install it?  If someone could do a step-by-step wifi driver  install for a U-touch (or at least regular Ubuntu) 15.x I'd be very very grateful.

I do not want to bridge the 722n, I want to use it instead of the  integrated card. Not even there yet, but just in case it matters.
Thanks!

---

