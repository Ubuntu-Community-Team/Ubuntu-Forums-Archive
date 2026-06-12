---
title: "No wireless after upgrade to Natty"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by akwusmc on 2012-03-26
I've been upgrading my distro from 10.04 to 11.04 (using Upgrade manager going by steps). When I got to 10.10, everything was working fine, including wireless. After I got to Natty, no wireless.

lspci returns:

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lsmod | grep b43 returns:

b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43

Synaptics Package Manager shows b43-fwcutter and firmware-b43-installer are installed, but the STA drivers and bcm-kernel-source are not.
 
But if I go to System>Administration>Additional Drivers, there are no proprietary drivers in use.

I've got a wired connection working, but wireless ... not so much.

Help!

TIA

---

