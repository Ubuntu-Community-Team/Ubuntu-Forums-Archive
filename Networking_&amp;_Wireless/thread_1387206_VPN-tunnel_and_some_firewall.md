---
title: "VPN-tunnel and some firewall"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by pold on 2010-01-21
I recently start using Ipredator (a VPL service). Apparently it decides to close the connection pretty constantly leading to my normal IP is 'out there'. The standard solution was to configure your firewall to block everything not going through the VPL. My question is how do I do that? Any free ubuntu-firewall works.

secondly it would be nice if my computer reconnected to the VPL automaticly after it gets disconnected. I have "auto connect" checked but it doesn't seem to matter.

---

### Post by DGortze380 on 2010-01-21
> **pold said:**
> I recently start using Ipredator (a VPL service). Apparently it decides to close the connection pretty constantly leading to my normal IP is 'out there'. The standard solution was to configure your firewall to block everything not going through the VPL. My question is how do I do that? Any free ubuntu-firewall works.

secondly it would be nice if my computer reconnected to the VPL automaticly after it gets disconnected. I have "auto connect" checked but it doesn't seem to matter.

This can cause some problems. You still need to allow normal network traffic to and from your machine. Things like DHCP requests.

iptables -P OUTPUT DROP

Will append and implicit deny to your output chain, thus dropping all traffic outbound from the machine.

You'll need to add additional rules to allow traffic you want.
I'm no sure what language this is, I certain don't read it. German Maybe?
[https://www.ipredator.se/faq/qna/](https://www.ipredator.se/faq/qna/)

Looks like you need ports 1723 and 47??

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by pold on 2010-01-22
maybe it's a better idea to block everything trying to communicate with my non-vpl ip. port 1723 should be open. 47 is a protocol thats necessary for hardware routers. Not a problem in my case.

I will read the iptables how to. thanks!

the language is swedish btw.

---

