---
title: "avahi across gateway"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by monoab314 on 2010-11-26
Hi all

I am wondering if it is possible to use avahi to resolve hostnames across a gateway.  With gateway I mean a linux box with ip_forward'ing enabled to pass traffic between interfaces.  The gateway connects two networks with all hosts running Ubuntu and specifically avahi-daemon.  The gateway is not running avahi and I am not able to install it there.  The firewall configuration on the gateway is not blocking any traffic between the networks.  I am able to send UDP packets from a host on one network to a host on the other.

When I run tcpdump on a host and try to ping that host.local from a machine on the other network I see no traffic.  This means that the gateway is not passing the multicast traffic along.  Is there any special setup required on the gateway to allow this?

Thanks!

---

### Post by redmk2 on 2010-11-26
> **monoab314 said:**
> Hi all

I am wondering if it is possible to use avahi to resolve hostnames across a gateway.  With gateway I mean a linux box with ip_forward'ing enabled to pass traffic between interfaces.  The gateway connects two networks with all hosts running Ubuntu and specifically avahi-daemon.  The gateway is not running avahi and I am not able to install it there.  The firewall configuration on the gateway is not blocking any traffic between the networks.  I am able to send UDP packets from a host on one network to a host on the other.

When I run tcpdump on a host and try to ping that host.local from a machine on the other network I see no traffic.  This means that the gateway is not passing the multicast traffic along.  Is there any special setup required on the gateway to allow this?

Thanks!

This will never happen.  Avahi allows programs to publish and discover services and hosts running on a local network only.  By local it means *only one subnet.*

You can read more about it [**_here _**]("http://avahi.org/wiki")and [**_here_**]("http://avahi.org/wiki/AboutAvahi#Details").

---

### Post by monoab314 on 2010-11-29
Thanks for the info.  I dug a little further and found avahi supports a "reflector" mode.  From the man page:

> enable-reflector: If set to "yes" avahi-daemon will reflect  incoming mDNS  requests  to all local network interfaces, effectively allowing clients to browse mDNS/DNS-SD services on all networks connected to the gateway.So this is possible but only if the gateway is running avahi-daemon also.  Won't work in my case but maybe someone else finds it useful.

Cheers

---

