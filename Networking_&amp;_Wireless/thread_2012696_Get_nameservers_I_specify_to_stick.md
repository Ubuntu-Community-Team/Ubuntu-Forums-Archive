---
title: "Get nameservers I specify to stick"
date: 2012-06-29
forum: Networking &amp; Wireless
---

### Post by taotree on 2012-06-29
I'm on latest ubuntu release. I use a VPN for work. In network manager, for both my normal wired connection, and for the VPN connection also, I have it configured to "Automatic (VPN) addresses only" and I specify the nameservers I want to use. But when I check /etc/resolv.conf after connecting to the VPN, it shows different nameservers. The problem is this causes a great delay in browsing the web because the VPN nameservers are either really slow or maybe it's even timing out.

How can I get it to stick to using the nameservers I specify?

If I edit resolv.conf and set it to the nameservers I want, the delay goes away, so I know this is the problem.

---

