---
title: "PPTP on VM?"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by rosefox911 on 2012-10-10
Hello all,

I have a bit of a strange request. I currently have Ubuntu 12.04 installed on my computer. I want to setup several VMs (Most likely debian) where each will be connected to a different PPTP VPN server. Is this possible? If so, how? Thank you!

Jorge

---

### Post by Lars Noodén on 2012-10-11
You might plan to use IPsec or OpenVPN instead.  PPTP was never known for security and recently had a [final nail in its coffin](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html).

---

### Post by Whoopie on 2012-10-11
BTW, if you use VirtualBox and configure networking as NAT, PPTP won't work as GRE is not supported when using [NAT]("https://www.virtualbox.org/manual/ch06.html#nat-limitations").

---

### Post by rosefox911 on 2012-10-11
Hey guys,

This is meant for an automated script, ideally, I would be able to pull from a pool of IPs. This is why I selected PPTP. I know its outdated and unsecure but that isn't related to what I want. I'd just like to be able to configure it so each VM has its own connection and is able to switch IPs on the fly without interrupting the other. Thanks!

---

