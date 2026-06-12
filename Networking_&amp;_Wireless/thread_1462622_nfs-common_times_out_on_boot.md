---
title: "nfs-common times out on boot"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by slooow on 2010-04-25
Hi all,

On booting, nfs-common stalls and then times out. I have nfs-common installed to act as nfs client. The firewall as iptables is stopping rpc-statd from connecting. 

Apr 26 09:36:34 ant rpc.statd[5779]: Version 1.1.2 Starting
Apr 26 09:39:34 ant rpc.statd[5779]: unable to register (statd, 1, udp).

In iptables I opened the port 111 for portmapper and in /etc/default/nfs-common I fixed the 
STATDOPTS to an unprivileged port to no avail.

When I turn iptables off, nfs-common starts without hitch. 

Is there anything I could do to make it work with iptables?

Thanks.

---

