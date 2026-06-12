---
title: "NIC multiple modes"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by Carlos Guimarães on 2011-02-24
Hi,

I've been looking for setting NIC to be able to monitor all traffic 
received from the wireless network, in order to capture layer2 packets 
without having to be associated with an AP or ad-hoc network.However, 
most drivers do not support connecting to a network while in monitor 
mode. And this is what I needed, i.e., be able to capture L2 packets and 
also have connectivity with some network.

Since Madwifi drivers supports VAP, a simple way to support it was to 
create a VAP for running in station mode and a VAP for running in 
monitor mode correct? But this way would be limited to Atheros NICs correct?

Any other suggestions to do this?

Thanks,
Carlos

---

