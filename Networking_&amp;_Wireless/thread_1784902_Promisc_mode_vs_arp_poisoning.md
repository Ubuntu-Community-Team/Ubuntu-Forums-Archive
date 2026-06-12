---
title: "Promisc mode vs arp poisoning"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by SlingerXL on 2011-06-17
I have a conceptual question. What's the difference between putting a NIC in promisc mode and arp poisoning a target especially in regard to info one can extract with wireshark. I thought promisc mode meant I could intercept, read, and capture all the packets in range of my NIC. I though this would mean I could capture with wireshark and then snag info like http passwords and urls with urlsnarf or tcpxtract but apparently not. 

All these apparently only work with arp poisoning. Is there some kind of encryption on packets that is undone by the router and target if their MAC addy's match up or something? WEP lan if it matters and I know/am using the WEP key when I'm sniffing in promisc. Can any interesting info other than dest/source and type of packet be read from just the promisc interface?

---

### Post by SlingerXL on 2011-06-19
Anyone know?

---

