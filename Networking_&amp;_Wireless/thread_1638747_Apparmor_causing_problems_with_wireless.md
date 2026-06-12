---
title: "Apparmor causing problems with wireless?"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by j2fraser on 2010-12-06
I am having real connection issues with my D-Link PCI wireless card (runs the ath9k driver). It was automatically detected and configured in Maverick (10.10) 64-bit.

I get a connection, but it is much more flaky than it was under 9.04. It disappears, then comes back sometimes, but more often than not I need to reconnect. I was using Network Manager, but switched to Wicd, hoping that would help, but to no avail...

My messages log shows:

> ADDRCONF(NETDEV_UP): wlan0: link is not ready
ath9k: Two wiphys trying to scan at the same time
wlan0: authenticate with ______ (try 1)
wlan0: authenticated
wlan0: associate with _____ (try 1)
wlan0: RX AssocResp from ______ (capab=0x431 status=0 aid=1)
wlan0: associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes readytype=1400 audit(1291564748.594:16): apparmor="DENIED" operation="open" parent=30992 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=31025 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

?? Is Apparmor interfering with DHCP, or is this another problem? Forgive my ignorance, but I tried the Googs, and got stumped! I saw some webpages relating to problems with redundant rt* drivers being loaded in the kernel, but I don't seem to have that problem... (I think).

Any help would be appreciated. Thanks!

---

### Post by j2fraser on 2010-12-07
Bump?

---

### Post by j2fraser on 2010-12-23
Bump?

---

### Post by goldenshale on 2011-02-20
Yeah, I'd like to hear about this too.  My wireless often has a tough time getting an IP address so I'm wondering if this error I see in dmesg is the cause...

Bump!

---

### Post by TimInCali on 2011-05-18
I found [this post]("http://opennomad.com/content/ubuntu-lucid-wicd-and-domain-name-servers") on resolving issues w/ apparmor and wicd.  It seems that WICD doesn't play well with apparmor, so you have to go through this quick step to resolve it.  Back up the config file first.  Good luck!

---

