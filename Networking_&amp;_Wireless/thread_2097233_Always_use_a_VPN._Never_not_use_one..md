---
title: "Always use a VPN. Never not use one."
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by H4rm0ny on 2012-12-22
Hi.

I am able to set up and use a VPN on my Linux box. What I want to do, is make sure that this box *always* uses that VPN connection and never doesn't not use it. Basically, the moment that machine gets a network connection, its first action should be to connect to the VPN and if that VPN connection drops, it should not be talking to the outside world until it can start the connection up again. I want all HTTP, DNS, whatever, to go via VPN. Basically for privacy.

Is this possible? In case it's relevant, the box is a VM running in Oracle's VirtualBox. I normally have it use a Bridged Connection to the host and it gets a local IP address via DHCP from my router.

How can I ensure that the box *only* uses the VPN, even if the VPN connection drops?

Many thanks!

H.

---

