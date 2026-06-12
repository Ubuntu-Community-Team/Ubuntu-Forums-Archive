---
title: "How configure wireless with Broadcom BCM4322 card ?"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by b&amp;m on 2009-11-13
Hi. I'm not able to configure wireless connections on my notebook HP 6735b.

The Network Controller is (as of 'lspci -nn' output): 

Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

I also activated the "Broadcom 43 wireless driver" from System>Administration>Hardware Drivers and restarted without success. No wireless connection is detected and displayed in the Wireless tab of the Network Connections window (that I open it via Edit Connections of NetworkManager Applet 0.7.996).

By the way, is normal that the NetworkManager icon isn't as decribed in the Help and Support page ?

<< Network Manager is the little icon in the system notification area in the top right of your screen.
        It looks like two over-lapping computer screens or four blue or grey stepped bars (when connected wirelessly). >>

Thanks in advance.

---

### Post by O1av on 2009-11-14
I have the exact same problems on a HP6735b laptop, with a similar broadcom card (BCM4312 802.11b/g)

I tried many of the guides and solutions regarding wireless connection and broadcom network cards, but with no results..

I would be very thankful for any suggestions as well.

**edit:** I managed to fix my problems somehow... I'm a complete ubuntu newbie, and i'm not sure what exactly i did.
(It may not have been the same problem though)
It might have been my attempts at following this guide: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
or me doing 'sudo apt-get update' and activating drivers from System -> Administration -> Hardware Drivers.
Or downloading this: [http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

Hope this can be useful somehow, although it might not be.

---

