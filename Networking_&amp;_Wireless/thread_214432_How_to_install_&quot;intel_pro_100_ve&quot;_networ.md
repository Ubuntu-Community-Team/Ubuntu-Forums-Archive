---
title: "How to install &quot;intel pro 100 ve&quot; network adopter"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-07-12
I have "intel pro 100 ve" network adopter. my cablenet server is using windows xp. tell me how can i install the driver for adapter and how to configure it in Kubuntu 6.06.
Regards
True_friend

---

### Post by mogelhead on 2006-07-21
Assuming it is the same card as Intel Ethernet Pro 100...

I think you should use the e100 kernel module.

[Wired Ethernet Troubleshooting Process]("http://ubuntuforums.org/showthread.php?t=87643")

Also there seems to be problems with the intel pro 100 cards.

kamsar solved it by passing the kernel the "noapic" option in [this thread]("http://www.ubuntuforums.org/showthread.php?p=159853").

Kilz explains in more detail howto do it in [this thread]("http://ubuntuforums.org/showthread.php?p=1214260").

---

