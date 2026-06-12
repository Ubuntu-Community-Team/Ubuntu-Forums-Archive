---
title: "ubuntu 9.04, wpn11.inf &amp; WARNING!"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by switcha on 2009-05-17
Ok folks.

Reloaded 9.04.
Installed updates.
Installed wpn11.inf as per said instructions i.e. using ndiswrapper.

Installed fine.
Picking up network (flashing blue).
Not connecting.

Here is what I get when I input:

sudo modprobe ndiswrapper

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

From what I gather that's a harmless message - [http://forums.debian.net/viewtopic.php?t=37581](http://forums.debian.net/viewtopic.php?t=37581)

But. This is still not helping me fix my problem.
I've set my router to accept both wpa + wpa2 psk security.

Here are the results of iwconfig:

lo    no wireless extensions.
eth0  no wireless extensions.
pan0  no wireless extensions. [huh??]
wlan0 IEEE 802.11g     ESSID:off/any
      Mode: Managed    Frequency: 2.437GHz    Acces Point: Not-Associated Bit Rate: 108 Mb/s   Power Management: off
Link Quality:0 Signal Level:0 Noise level:0  Rx Invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0 Tx execessive retries:0 Invalid misc:0 Missed beacon:0

Any ideas please folks?

---

### Post by switcha on 2011-02-26
Issue resolved with latest edn.

---

