---
title: "Internet vs VPN"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Kom-Si on 2008-12-04
I configured VPN in Ubuntu 8.10 through Network Manager. Everything's fine, it connects to my workplace network.

But when VPN is up I can't use Internet, e.g. Firefox. It's a well know problem, in Wondows it's cured by unchecking the 'Use defail gateway' option in VPN's TCP/IP properties.

I'm new to Linux, and I didn't figure out how to set up proper routing to enable both I-Net and VPN simultaneously. A walk-through reply would be much appreciated.

Details: my ISP provides me with a fixed IP address which I enter into my eth0 manually whereas my work VPN server gives me a dynamic internal IP address.

Thanks for help.

---

### Post by superprash2003 on 2008-12-04
when connnected to vpn post output of cat /etc/resolv.conf and output of ping 209.85.171.100

---

