---
title: "Monitor mode, injection, stability w/ Atheros cards"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by antareus on 2009-03-25
Hi,
At the end of my patience dealing with Madwifi stability issues. We were using Hardy w/ Madwifi 0.9.4 + a few Madwifi trunk patches backported. Now, I hard lock very consistently. It usually happens when one card is associating to a network at the exact same time another card is associating to another network. Or if one card is shutting down Kismet while another one is doing the same.

I'm looking for the most stable drivers that support monitor mode and packet injection. In other words, drivers that just work. I'm not averse to upgrading to 8.10, but ath5k doesn't look like a silver bullet here.

Trunk versions of Madwifi tend to just lock 8.04 very quickly, along with tainted messages in dmesg output.

---

### Post by BkkBonanza on 2009-03-25
I'd suggest asking at, 

[http://forums.remote-exploit.org](http://forums.remote-exploit.org)

Lots of keen people there.

---

