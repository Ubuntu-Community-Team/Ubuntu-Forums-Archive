---
title: "Is there any way to have to wired interfaces in WICD?"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by Manthis on 2009-07-03
Hi,

I'd like to know if there is any way to get my two wired network interfaces in wicd. I'd like to be able to have both eth0 and eth1 managed by this network manager.

Is it possible?

Thx

---

### Post by Cuppa-Chino on 2009-07-04
yes just go into the preferences, put the name of your wired interface in and then tick "always show wired interface at the bottom:

---

### Post by t0mppa on 2009-07-04
That applies for one wired interface, but the question was about two different wired interfaces. And last I checked, WICD doesn't support that, largely because the design they adopted at the beginning, where it focused upon only enabling one connection (ie. either wired or wireless) at a time, not to even mention multiple interfaces.

There are some works in progress towards this (like [VPB]("http://wicd.sourceforge.net/moinmoin/VeryPluggableBackends")), but nothing official as of yet, if I'm not mistaken.

---

### Post by Manthis on 2009-07-04
Well that's quite disappointing since I really need to be able to use two different wired connections. 

Well I know the NetworkManager can do that but I can't use it because I'm encountering to many instability issues with my AR928X Wifi card...

Too bad... I'm gonna have a look VPB anyway, or create a script to dynamically change the eth interface. Thanks for your help t0mppa ;)

---

