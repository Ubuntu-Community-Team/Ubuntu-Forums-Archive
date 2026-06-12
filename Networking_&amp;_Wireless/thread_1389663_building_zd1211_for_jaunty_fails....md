---
title: "building zd1211 for jaunty fails..."
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by beyossi on 2010-01-24
Hi all,

I tried many posts for building zd1211b driver.
I need to setup by Belkin USB wifi dongle as master ([https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)).
it looks like zd1211rw doesn't support master mode and I shall insmod the zd1211b driver.

however I couldn't install the driver with my jaunty.
I should not upgrade/downgrade my jaunty.

there are many errors which looks like incompatible kernel compared to the driver expectations.
for example (there are more): 
    error: too few arguments to function ‘iwe_stream_add_point’
    error: ‘struct sk_buff’ has no member named ‘mac’
    error: ‘struct driver_stats’ has no member named ‘iw_stats’

my headers are installed and i tried using modules-assistance but it results with the same errors.

Please help,
How can I install those zd1211 drivers into my jaunty machine????

Thanks

---

