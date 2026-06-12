---
title: "Network drivers testing Using Linux Test Project (LTP)"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by Yesubabu_Gude on 2013-08-01
Hi,

I want to test the Linux Network Drivers (Ethernet Controller) using LTP (Linux Test Project), So i downloaded the LTP Source code and installed it. I don't know to run the network tests in LTP.... If any one have idea please suggest me and thanks in advance.

---

### Post by Wayne_Shumaker on 2013-08-01
See [http://ltp.sourceforge.net/documentation/technical_papers/node3.php](http://ltp.sourceforge.net/documentation/technical_papers/node3.php)
There is a network.sh script, but I have not used it yet. Network testing usually requires two machines. 
Also check out [http://www.kriskinc.com/intel-pod](http://www.kriskinc.com/intel-pod) and how to use tcpreplay

Of course it depends on what you want to test. I have a motherboard, DQ77KB, with intel 82574L and an 82579LM network adapters. The 82579LM has had a lot of problems dropping packets and failing with "Detected Hardware Unit Hang". I downloaded and built the latest e1000e drivers and am also in the process of testing them.

---

