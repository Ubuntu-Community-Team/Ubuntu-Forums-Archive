---
title: "network detection"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by zeek333 on 2009-09-28
Hi,
I have small prob with network detection. I'm using ubuntu server 9.04. This server is connected to router with dhcp. 

Problem is when server is booted on I checking with ifconfig - ip assigned but my BIND9 and HEARBEAT can't detect network connection only when i restart bind9 and heartbeat they work. Also i noticed problem with resolv.conf it's reconfigure settings it self after each restart.In /etc/dhcp3/dhclient.conf i changed line  prepend domain-name-servers 1.2.3.4;

my interfaces file: 
```

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```and my resolv.conf
```

domain mydomain.com
search mydomain.com
nameserver 192.168.1.254
nameserver 1.2.3.4

```does any1 have an idea about this?

---

