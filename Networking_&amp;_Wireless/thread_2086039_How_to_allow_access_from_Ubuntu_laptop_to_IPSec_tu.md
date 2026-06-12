---
title: "How to allow access from Ubuntu laptop to IPSec tunnel between two routers?"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by Magnificent 7 on 2012-11-19
Hello,

I have the following scenario: Home country network, Netgear DG834Gv3 local IP address 192.168.3.1 local subnet 192.168.3.0 configured to permit inbound IPSec connections. Remote country, D-link DSL-2750U connected via PPPoE, remote IP address 192.168.1.1 remote subnet 192.168.1.0 configured to establish outbound IPSec tunnels to home country on home WAN IP address.

I am in the remote country and have successfully configured an IPSec tunnel from the DSL-2750U to the DG834Gv3. How do I now point the Ubuntu laptop at the established router-to-router IPSec tunnel? I have a feeling that it is somehow connected with changing the default gateway configured in /etc/network/interfaces on the laptop from 192.168.1.1 to 192.168.3.1, or at least adding this. But have spent 2 days scouring around for an unambiguous answer to this seemingly straightforward scenario.

From remote country on subnet 192.168.1.0, I can ping home router 192.168.3.1 and even access the DG834Gv3's router management interface webpage, by typing 192.168.3.1 into a browser URL box and entering username and password. So I am very close, and only missing the last step to have Ubuntu route all outbound traffic via 192.168.3.1 in my home country and away from the prying eyes of those monitoring the transparent proxies in remote country.

Thanks for any hints and tips.

PS: Following the advice of some how-tos, the local subnet on the DG834Gv3 was changed from 192.168.1.0 to 192.168.3.0 so as not to confuse the tunnel setup process.

PPS: Static routes and policies can be set up on the DSL-2750U in remote country and of course on the DG834Gv3, but I have not touched these yet and prefer a solution based around configuration changes that let the laptop direct traffic at home gateway 192.168.3.1.

---

