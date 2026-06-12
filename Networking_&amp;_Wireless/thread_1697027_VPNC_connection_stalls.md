---
title: "VPNC connection stalls"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by iulian on 2011-02-28
Hi,

I use VPNC to connect to a Cisco VPN. I am able to connect, but some issues exist when I use SSH. For example, I login through SSH to a computer in the VPN and I execute ls => it works. If I execute ls -la => connection stalls. I think it stalls every time it is supposed to return more content (top, ls /etc).

If I do scp from my end to server => works.
If I do scp from server to my end => connection stalls.

Advices are greatly appreciated.

Iulian

---

### Post by iulian on 2011-02-28
Solved.

I needed to decrease the MTU from 1412 to 1350.

Source: [http://www.lug-norderstedt.de/portal/downloads/anleitungen/vpnc_howto_v1_1_en.pdf](http://www.lug-norderstedt.de/portal/downloads/anleitungen/vpnc_howto_v1_1_en.pdf)

---

