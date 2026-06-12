---
title: "How do I set segmentation offload at startup?"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by GoalArt_Ulf on 2011-11-17
Hello,

I have a problem with segmentation offload in my virtual Ubuntu 10.04 gateway.

I need to run "ethtool -K IFNAME tso off gso off" at startup. I can not for my life sort out how NetworkManager and init and friends cooperate (or not) to control the interfaces.

I have tried to edit the file /etc/network/if-pre-up.d to add the desired ethtool command
but that didn't work too well. The segmentation offload got turned on anyway.

Any help would be appreciated.

TIA

  /Ulf Andersson

---

