---
title: "Very very wierd issue."
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by viktor.skarlatov on 2009-10-22
Hello

I have a rather perplexing issue. I have set up a small home network with 2 PCs and a laptop. The two PCs run FreeBSD and Ubuntu, the laptop (from which I am writing) also runs Ubuntu. The computers are all connected to the net via a Linksys WRT54G router, the laptop uses wireless and the PCs are wired. The connections are setup manually. The Ubuntu PC has an IP of 192.168.0.2, the BSD machine is 192.168.0.4 and the laptop is 192.168.0.3. The net mask is 255.255.255.0 and the only DNS server is provided by my ISP, it's IP is 78.90.3.1 and finally the router serves as the gateway and it's IP is 192.168.0.1.

Now with the network configuration out of the way, everything works perfectly fine, until the PC running Ubuntu starts up. After that (my guess) something happens to the router and no matter what I do, all other machines get cut our from the net. Firefox stays on Looking up [www.websitename.com]("http://www.websitename.com") and that's it.
Ping returns Destination host unreachable if I try to ping the Ubuntu PC. The router answers ping but nothing else works.

Any suggestions are greatly appreciated.

[SOLVED] I had a typo in the network address of the Ubuntu PC. Instead of 192.168.0.2 it was 192.168.0.1 (the same as the router).

---

