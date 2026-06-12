---
title: "bcm4312 help"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by korvirlol on 2009-11-07
Hello,

Ive been banging my head against the wall trying to get:

```
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```working. Ive reinstalled karmic several times from the cd, with no luck whatsoever. I followed the guide on the howto (buried somewhere in this forum) which installs the firmware and linux backports, blacklists some unneeded drivers. Ive also tried the suggestion of installing bcmwl-kernel-source.

Anyways, now the little light on my computer for wireless doesnt even turn on, lspci shows it and i have no idea what the next step should be in getting this to work. 

My computer is a dell vostro 1320, with the above wireless chip on 14e4:4315.

Ive been through the output of dmesg line by line several times, and there isnt even a mention of b43, bcm or anything. 

Any help anyone can provide would be GREATLY appreciated.

---

### Post by korvirlol on 2009-11-07
actually, this is in dmesg, not sure what it means, or even if it is relevant:
```

[    5.632697] lib80211: common routines for IEEE802.11 drivers
[    5.632701] lib80211_crypt: registered algorithm 'NULL'
[    5.876934] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.876939] Disabling lock debugging due to kernel taint
[    5.877593] wl: disagrees about version of symbol lib80211_get_crypto_ops
[    5.877595] wl: Unknown symbol lib80211_get_crypto_ops

```

please help :(

---

