---
title: "Problem connecting wireless with static IP"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by parthamage on 2010-11-18
All,
I have been having no issues connecting wireless with DHCP.  However, at my current location, the one wireless connection strong enough is from our USO (I'm at Camp LSA, Kuwait), and they use a static IP configuration.  At first I was having a problem getting the gateway address to stick, but found the answer to that in another forum.  Problem is that although I connect to the network, I am not receiving any packets, and not able to ping the router.  I am able to go to the Windows partition and connect, but would prefer to get it running in Ubuntu.
Please advise.

---

### Post by chili555 on 2010-11-18
If you are not receiving packets, I doubt you are connected. You have an IP address because you specified it, not because the router agreed.

Did you set up the static details manually in /etc/network/interfaces or in Network Manager? Did you also specify DNS nameservers? Is encryption involved? Would you please tell us what's been filled in, disguising the actual numbers, of course? Are the numbers identical to those in Windows; that is, specified by the USO?

---

