---
title: "Question on Router OpenDNS vs PC OpenDNS"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-13
Hi.
If a router has OpenDNS, then do the computers behind that router also have to have OpenDNS setup on each individual machine or does the router OpenDNS override the DNS settings of the computers?

---

### Post by steeleyuk on 2009-02-13
It depends. You can point the machines at the router and it will use the routers DNS settings. Alternatively, you can override the DNS settings of the router by manually inputting the DNS settings on the machines.

---

### Post by Rytron on 2009-02-13
> **steeleyuk said:**
> It depends. You can point the machines at the router and it will use the routers DNS settings. Alternatively, you can override the DNS settings of the router by manually inputting the DNS settings on the machines.

Hi steeleyuk. What do you mean by 'You can point the machines at the router'?

---

### Post by kevdog on 2009-02-13
Your /etc/resolv.conf file has the IP addresses of the dhcp servers.  You can list up to 3.  If you are using dhcp however, these entries will be changed by the dhcp server. In this case you would need to modify:
/etc/dhcp3/dhclient.conf

Here is a tutorial how to do this:
[http://ubuntu-tutorials.com/2008/06/17/enhance-your-network-connection-with-opendns/](http://ubuntu-tutorials.com/2008/06/17/enhance-your-network-connection-with-opendns/)

---

