---
title: "Noob. Network Messages: Code: 00 55 89 e5 0f 1f 44 00 00 fa 5d c3 90 8d 74 26"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by MrPeter on 2011-04-07
Hi,

I was hoping someone could help me with these messages that are driving me crazy. 

I am totally new to Linux and have just installed ubuntu 10.10. After configuring the network interface via dhcp I started getting these messages that come in so frequently I can't configure anything else. 

[87.186415] Stack:
[87.187406] Call Trace:
[*********] Code: 00 55 89 e5 0f 1f 44 00 00 fa 5d c3 90 8d 74 26 00 55 89 e5 0f 1f 44 00 00 fa 5d c3 90 8d 74 26
00 55 89 e5 0f 1f 44 00 00 fa 5d c3 90 8d 74 26 00 55 89 e5 0f 1f 44 00 00 fa 5d c3 90 8d 74 26 

Would anybody be able to shed some light on why I am getting this messages and more importantly how do I get rid of them.

The installation is on a VM on Hyper-V.

---

### Post by MrPeter on 2011-04-10
Okay now,

Found the answer if anyone needs it.

The problem was with the network interface I was using in Hyper-v. Changed the NIC to the legacy network controller and reinstalled ubuntu. You might be able to just reinstall the NIC but I'm a noob and just went straight for the full reinstall.

---

