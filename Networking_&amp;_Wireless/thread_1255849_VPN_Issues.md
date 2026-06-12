---
title: "VPN Issues"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by xenogia on 2009-09-01
Hi Guys,

I am trying to connect to my work VPN through the use of openvpn and network-manager-vnpn.  Anyway it says it connects but when I try to browse any of the vpn sites in firefox it says connected to blah.blah.blah but doesn't move from there.

What steps do I need to do to resolve this issue?
And what do you have to show you guys to get this to work?

I really hope someone can help.

Best Regards,
Dean

---

### Post by jonobr on 2009-09-02
Hello


When you say it says connected, do you mean your connecting via an intranet to a website and it comes up blank, or something similar?

Can you ping these sites through your VPN?

If so, maybe you need to check the MTU size with your admin,
MTU sizes can be problematic across VPNs.
The default ethernet is usually 1500, you can see this by doing a ifconfig in a terminal window.

Sometimes reducing this can work better but again, working with your admin, he may provide some info into that

---

