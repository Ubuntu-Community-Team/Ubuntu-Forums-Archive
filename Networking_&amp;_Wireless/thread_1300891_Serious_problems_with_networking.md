---
title: "Serious problems with networking"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by turgidtoupee on 2009-10-25
At first my internet connection kept disconnecting randomly. I have a netgear wg111v2 adapter. I was told to try wicd instead of network manager, which I did. Wicd couldn't detect any wireless networks, so I reinstalled network manager. Now, network manager won't show any wireless connections, even the tickbox to enable wireless is gone. Is there a way to get it back?

---

### Post by Iowan on 2009-10-25
Though I don't understand why it would disappear...
Check **lshw -C network** to verify that the wireless card gets an alias and driver.

---

