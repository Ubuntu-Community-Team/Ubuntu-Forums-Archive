---
title: "Dbutils finds channels, but MythTV don't"
date: 2008-06-20
forum: Multimedia Software
---

### Post by RipperDoc on 2008-06-20
I am using Mythbuntu 8.04 and an HVR-1110 DVB-T card. Using the dvbutils and latest firmware for that card, I have managed to scan for and lock on channels, using the commands w_scan and tzap.

However, when I startup the MythTV configuration utility, all scans fails - even when I try to import the same channels.conf file that tzap successfully uses. What could be the difference between these two?

Thank you in advance,
Martin

---

### Post by dibuntux on 2008-10-15
Almost the same using an HVR1100. I can scan and get a lock on some networks, but not on others (Mediaset2 network) that are found using the scan from dvb-t utils. 
Channelconf import also DOES NOT WORK for dvb-t, but it does work for dvb-s.
And of course, yes VLC can lock on those channels, as did myth 7.10...

Conf:
Mythbuntu 8.10 beta 
Ahtlon 1700+ 512MB
Nvidia 5200
Hauppauge HVR1100
Technisat SkyStar 2.6

---

