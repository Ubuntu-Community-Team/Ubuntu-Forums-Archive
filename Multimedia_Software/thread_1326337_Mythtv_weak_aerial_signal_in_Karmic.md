---
title: "Mythtv weak aerial signal in Karmic"
date: 2009-11-14
forum: Multimedia Software
---

### Post by PaulRSte on 2009-11-14
Since upgrading to 9.10 (64 bit) the aerial signal has been very weak in mythtv.  It starts off fairly reasonable (58%) after a reboot but gradually drops off and has been as low as 2%.  Once it gets below 48% then the system won't lock onto it.
The only thing I've managed to find so far is to rename /etc/modprobe.d/options to options.conf to ensure that the low noise amplifier is getting turned on.  For various reasons I created a new file but then found that modprobe was still using the old one.  I renamed it to options.old but modprobe still picked up the old one so I finished up deleting it.
Question is, how do I know if it is picking up the settings correctly as the situation hasn't improved.
Note that the system was working fine prior to the upgrade from 8.04.
Regards - Paul

---

### Post by PaulRSte on 2009-11-28
Still getting problems with this.  Funnily enough it ran fine for about 2 weeks and then lost the aerial signal again - down to 2%.  Rebooted and ok again.  Can anyone help e.g. where do I start looking to see what is happening?

Thanks

---

