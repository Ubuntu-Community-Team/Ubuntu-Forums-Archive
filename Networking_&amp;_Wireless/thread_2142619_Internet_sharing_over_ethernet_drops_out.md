---
title: "Internet sharing over ethernet drops out"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by ethanoldale on 2013-05-06
I have just installed 13.04, and one of the first things I did was share my wifi connection over eth0 with network manager.
It worked for about a minute, but then stopped, without ubuntu even letting me know.

im not sure where to start, but here is the bottom of dmesg, after internet sharing stops working
```
[  493.090637] ip_tables: (C) 2000-2006 Netfilter Core Team
[  493.125164] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  561.888588] systemd-hostnamed[2520]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  615.535553] cfg80211: Calling CRDA to update world regulatory domain
[  615.546633] cfg80211: World regulatory domain updated:
[  615.546643] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  615.546650] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  615.546656] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  615.546662] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  615.546667] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  615.546672] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  618.656645] atl1c 0000:08:00.0: irq 45 for MSI/MSI-X
[  618.656865] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  709.014241] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
```

Any help would be appreciated

---

