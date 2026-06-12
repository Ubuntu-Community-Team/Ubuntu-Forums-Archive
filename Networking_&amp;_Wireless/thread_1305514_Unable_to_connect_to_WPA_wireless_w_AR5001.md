---
title: "Unable to connect to WPA wireless w/ AR5001"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by Nakor BlueRider on 2009-10-29
Hey,

I have an AR5001 card, started out with 9.04.  Tried several setups (default driver, the backports, ndiswrapper) and had similar problems with them all.  After choosing to connect and entering in the password, I would get the first green light, then the second, and then several seconds after that it would say "Wireless connection disconnected."

I tried the upgrade to 9.10 and am having basically the same problem.  (I also wound up with the "wireless is disabled" problem, but the workaround of disabling and reenabling ath5k several times seems to work, however frustrating it may be.)  I see the network, start to connect, it appears to accept the password, and then several seconds later disconnects.

At the moment I've removed all trace of ndiswrapper and backports (which I did try on 9.10 as well without success), and am running compat-wireless-2.6 which seems to have been the closest to working out of the bunch.

128-bit WEP seems to work okay, but I'd rather use WPA of course.  Any ideas on this one?

---

### Post by deimios on 2009-11-17
Same here. AR5001 (rev 1) with driver ath5k and it fails to connect to WPA.

---

### Post by deimios on 2009-11-17
Solved by using madwifi: [http://ubuntuforums.org/showthread.php?t=1163380]("http://ubuntuforums.org/showthread.php?t=1163380")

---

### Post by bourger on 2010-02-07
Confirm the problem.
I've got EeePC 1000HE, Ubuntu 9.10 and use ndiswrapper.
Although my home WPA network parameters are stored in network manager, I **always** have to re-enter the password after reboot or suspend mode. Connections to other WPA networks are unstable, with accidental breaks or sudden password requests.

---

