---
title: "TC and tcpdump problems on ppp Interface"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by CAntoine on 2011-07-05
Hello,

I am working on an ppp interface (Link type: LINUX_SLL), trying to implement a TC qos on it. And I have got some problems.

With wireshark, I see DNS packets and PPP LCP packets. But with tcpdump and tc, I can only see the DNS packets.
With a ifconfig ppp1, I can see the RX and TX number of packets increasing when I see a PPP LCP packet on wireshark. But nothing with tcpdump neither tc.

Does anybody got any idea what is going on, and how to solve the problem (to "see" the PPP LCP packet with tc)

Thx

---

