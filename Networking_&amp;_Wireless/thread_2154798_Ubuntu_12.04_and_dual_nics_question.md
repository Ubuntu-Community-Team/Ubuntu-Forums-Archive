---
title: "Ubuntu 12.04 and dual nics question"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by lionlike on 2013-06-15
Here's my scenario... I have two nics in a server.  Eth0 has a static routable IP and connected to the Internet.  Eth1 has a static private IP and is connected to a private network internally.  I've read several blog posts about doing post-up route adds and deletes and nothing seems to work... consistently.  Here's my /etc/network/interfaces file:

auto eth0
iface eth0 inet static
        address x.x.x.40
        netmask 255.255.255.0
        network x.x.x.0
        broadcast x.x.x.255
        gateway x.x.x.1
        dns-nameservers x.x.x.2
        post-up route add default gw x.x.x.1
        post-up route add default gw x.x.x.40 dev eth0


auto eth1
iface eth1 inet static
        address 192.168.32.40
        netmask 255.255.255.0
        network 192.168.32.0
        broadcast 192.168.32.255
        gateway 192.168.32.1
        post-up route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.32.1
        post-up route add -net 172.16.0.0 netmask 255.240.0.0 gw 192.168.32.1
        post-up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.32.1
        post-up route del default gw 192.168.32.1
        post-up route del -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.32.1
        post-up route del -net 172.16.0.0 netmask 255.240.0.0 gw 192.168.32.1
        post-up route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.32.1

What I'm trying to accomplish is force all internal IP traffic through eth1, and have a default route to the Internet through eth0 for all other traffic. Our intranet contains various routers and uses multiple ranges of private IPs - including access to NFS storages, database, etc.  I want to force all this internal traffic through eth1.  Unfortunately, it seems like the OS picks at random each time it boots as to which eth becomes the default gateway despite the above config.  A route -n one minute will result in 0.0.0.0 destined for x.x.x.1 out of eth0, and the next boot it'll be 0.0.0.0 destined for 192.168.32.1 out fo the eth1 interface - and of course then the server can no longer be reached from the Internet, because the default route is saying "if I don't know where to send it, go through eth1, which ends up in a non-routable network..

Any thoughts?

---

### Post by newbie-user on 2013-06-16
The "gateway" line assigns the default gateway. By having a "gateway" line for both eth0 and eth1, you're specifying that the server has two default routes. Remove the "gateway" line from eth1 and it should work.

---

