---
title: "VPN-server setup, ipalias bug"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by aztekk on 2012-01-11
I'm trying to set up a pptp-server on my box, that's on my LAN, behind a NAT router.
Due to bug#[876829]("https://bugs.launchpad.net/ubuntu/oneiric/+source/ifupdown/+bug/876829"), I'm having a hard time doing this, since my server only has one NIC and ipalias on a single NIC is currently broken in Oneiric.

The idéa with my VPN, is for me to use with my iphone, to access my own private DNS-server @home and other things, when I'm away from home.

Does anyone have a alternative method to solve my issue?

My server behind a router, on a 192.168.1.0/24 network.

ps. router does not support ipsec passthrough =/

---

### Post by gordintoronto on 2012-01-11
Which one do you need, a VPN server or a pptp-server? I think you only need VPN? 

What version of Ubuntu are you using? Do you understand Port Forwarding? Do you use dnydns or a similar service to get to your router from the Internet? Does your ISP allow you to operate a server?

---

### Post by aztekk on 2012-01-11
> **gordintoronto said:**
> Which one do you need, a VPN server or a pptp-server? I think you only need VPN? 

What version of Ubuntu are you using? Do you understand Port Forwarding? Do you use dnydns or a similar service to get to your router from the Internet? Does your ISP allow you to operate a server?

Please explain the difference between VPN and pptp-server?

- I'm running 11.10 oneiric.
- I know portforwarding.
- Dyndns yes
- no, but they don't block ports etc .. I got that covered.

---

### Post by gordintoronto on 2012-01-11
Oh shucks, the bug looks like the problem. I totally failed to get a working connection to a VPN server in Oneiric, then got one running in about five minutes in some other windowed operating system.

---

