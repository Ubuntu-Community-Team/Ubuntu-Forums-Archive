---
title: "[Wireless] Asus EeePC 1000HE Ubuntu 9.04 - Install madwifi driver instead of ath9k"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by FabiettoErMejo on 2009-05-28
hi at all. i'm newbie in linux and i have a problem with my wireless net at home. i've lost my router's password some time ago and after updating ubuntu from 8.10 to 9.04 i've also lost wep key. now since i love experimenting with wireless and because i've to retrieve my wep key, i need to install madwifi driver (with patch for packet injection - if i've not understood bad -) with aircrack-ng to do this job. when i wrote from my desktop pc, i've installed ath9k driver on eeepc, so i need to remove this and install madwifi. can someone help me [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/huh.gif[/IMG]

thanks in advance and sorry for the bad english

---

### Post by t0mppa on 2009-05-28
If you only need it for the packet injection, then you're making things a bit too hard. Since ath9k uses mac80211 to run monitor mode and mac80211 does have injection support, see [here]("http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git;a=blob;f=Documentation/networking/mac80211-injection.txt;").

If you really need the madwifi drivers though, there's two options. Go to System / Administration / Hardware Drivers and it should be listed there as a proprietary driver that you can just activate. Or then you can download the binaries from [here]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz") and compile it manually.

---

