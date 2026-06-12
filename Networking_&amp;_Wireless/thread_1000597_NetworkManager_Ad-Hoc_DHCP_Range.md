---
title: "NetworkManager Ad-Hoc DHCP Range"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Picchioni on 2008-12-03
Hi all,
I'm new to the Ubuntu forums and am looking for a little help with NetworkManager.

I'm wondering if it's possible to choose the IP address range that NetworkManager uses when creating an Ad-Hoc network?

I'm basically trying to tether my iphone to my laptop which requires an Ad-Hoc network. When the iPhone connects to a wireless network and pulls a 165.254.x.x ip address, it assumes that it will receive no internet access and uses the cell network for the internet connectivity while connected to the wireless network. I can then run a program that does some magic behind the scenes that allows machines connected to the Ad-Hoc network to leach internet access off the iphone.

However, when it receives an address of 10.x.x.x (which is what NetworkManager uses for its Ad-Hoc IP Range) it assumes a perfectly good wireless network and refuses to flip over to the cell network for internet connectivity.

So I'm wondering if there's a way to force NetworkManager to use a specific IP range for the Ad-Hoc network?

Thanks.

---

