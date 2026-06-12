---
title: "Network Manager stops working when gateway and DNS IP adresses are different"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by Strange_Movement on 2010-05-14
Has anyone else noticed that if you use a standard install of Lucid Lynx 10.04 with Network Manager getting the IP address from a DHCP server that provides a gateway and DNS IP address that are not the same, name resolution does not work.

At work we have a DHCP server that provides a gateway address of 192.168.0.6 and a DNS address of 192.168.0.3 . All other machines running any other operating systems work perfectly however two entirely different machines running 10.04 can no longer resolve domain names. They do with previous versions of Ubuntu and Windows but they won't with Lucid Lynx. If you assign IP settings manually in Network Manager they still don't work. However if you assign IP settings manually using **/etc/network/interfaces** and **/etc/resolv.conf** then run **/etc/init.d/networking restart** they work perfectly.

Is this a failure of the Network Manager App ?

I don't know enough of where and how to look for answers, or if/where/how to report this as a bug.

Can anyone advise me please ?

---

### Post by McRat on 2010-05-14
> **Strange_Movement said:**
> Has anyone else noticed that if you use a standard install of Lucid Lynx 10.04 with Network Manager getting the IP address from a DHCP server that provides a gateway and DNS IP address that are not the same, name resolution does not work.

At work we have a DHCP server that provides a gateway address of 192.168.0.6 and a DNS address of 192.168.0.3 . All other machines running any other operating systems work perfectly however two entirely different machines running 10.04 can no longer resolve domain names. They do with previous versions of Ubuntu and Windows but they won't with Lucid Lynx. If you assign IP settings manually in Network Manager they still don't work. However if you assign IP settings manually using **/etc/network/interfaces** and **/etc/resolv.conf** then run **/etc/init.d/networking restart** they work perfectly.

Is this a failure of the Network Manager App ?

I don't know enough of where and how to look for answers, or if/where/how to report this as a bug.

Can anyone advise me please ?

Naw, I'm pretty sure that works.  My machine at home is setup that way.  It has DHCP for LAN, but it uses 4.2.2.2 as DNS.  My Cable Company has a TERRIBLE DNS.

---

### Post by McRat on 2010-05-14
This is a U32 10.04 machine on gbit ethernet card.

I changed it to Autcmatic DHCP (Address Only) under IPv4 menu, then added my DNS IP.

It did not work at first.  I rebooted, then it saw the LAN again.  Seems a bit more sluggish though.

---

