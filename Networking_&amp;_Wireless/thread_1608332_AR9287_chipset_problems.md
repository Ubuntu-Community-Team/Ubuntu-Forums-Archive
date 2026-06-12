---
title: "AR9287 chipset problems"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by z987k on 2010-10-28
I'm having a problem with this chipset on 10.10.
AR9287 wireless network adapter on an acer 5742G-7200.

Wireless is cutting(disconnecting) out or just dropping everything while not actually disconnecting every so many minutes and if I download large files or keep the computer up for a long period of time, it gets really bad - as in every 1 min or less or everything stops responding(online).

I installed linux-backports-modules-wireless-maveric-generic-pae as suggested elsewhere, as this seemed to be a fix for 10.04.

 uname -r yields 2.6.35-22-generic-pae.

dmesg | tail right after a drop:

```
[ 2503.438472] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 1)
[ 2503.635642] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 2)
[ 2503.835509] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 3)
[ 2504.035889] wlan0: authentication with 22:1d:60:d3:a0:c3 timed out

```

I boot into windows and the wireless works fine.  It seems to be if I download any large file, the network just plain stalls.

Further, the best I get speed wise in 10.10 is about 50k/s even over the network.  In windows I get close to N speeds and 200k/s over the net.

---

