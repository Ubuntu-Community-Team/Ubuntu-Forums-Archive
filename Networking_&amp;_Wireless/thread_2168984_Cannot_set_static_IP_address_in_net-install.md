---
title: "Cannot set static IP address in net-install"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by yannick2 on 2013-08-20
Hi,

I'm trying to install ubuntu on a server using net-install, remotely.
I have no choice to use net-install.

My IP is static. I have a problem. The DHCP autoconfiguration fails. In fact ubuntu install "thinks" it's ok but it's not.
So I redo "configure the network" and... well, I cancel most auto config part and it then asks me to configure the network manually which i do.
However, it's quite idiotic, as the manual config menu doesnt prompt me for the broadcast IP. It sets the broadcast IP in /etc/network/interfaces to x.x.x.47, while I need x.x.x.48
And obviously, I cannot download any package because of this.

No ifconfig either, it's a very minimal CD. I'm stuck.

WHat the hell can I do?

Thanks (a lot!)

---

