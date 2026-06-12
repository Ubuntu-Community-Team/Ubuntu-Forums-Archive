---
title: "Big problems with rt2870 on intrepid"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by nknico on 2009-04-01
I follow this tutorial to install the rt2870 driver on intrepid :
[http://ubuntuforums.org/showthread.php?t=919044](http://ubuntuforums.org/showthread.php?t=919044)

The driver's version present on the ralink's site ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)) changes from 1.4.0 to 2.1.0...

Compilation works fine...

But after reboot, NetworkManager and Wpa_supplicant are both taking 100 % of the CPU.
The connection to the network is impossible.
And the /var/log/messages is full of messages like theses ones : 

```
Apr  1 16:43:26 nico-laptop kernel: [ 1239.454584] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=1!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.454592] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=2!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.469205] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=3!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.469213] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=4!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.478648] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=5!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.478870] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=6!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.498929] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=7!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.498936] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=8!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.508120] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=9!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.508343] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=10!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.516875] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=11!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.516883] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=12!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.521227] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=13!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.521235] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=14!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.530090] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=15!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.530098] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=16!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.536284] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=17!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.536292] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=18!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.541294] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=19!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.541302] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=20!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.545852] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=21!
Apr  1 16:43:26 nico-laptop kernel: [ 1239.545860] Qidx(0), not enough space in MgmtRing, MgmtRingFullCount=22!
```

---

### Post by nickmcg on 2009-04-01
You could try deleting /etc/Wireless/RT2870STA/RT2870STA.dat

That worked for me, as did moving to Jaunty, where the rt2870 worked out of the box!

HTH

Nick

---

