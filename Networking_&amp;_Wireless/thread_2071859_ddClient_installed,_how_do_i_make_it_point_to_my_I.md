---
title: "ddClient installed, how do i make it point to my IP address?"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by MortenSJ on 2012-10-16
Hi

This is my first Ubuntu server so i'm quite new to this.

I setup my Ubuntu server so that it has a static ip. 10.0.1.20

I get a dynamic ip from Time Warner Cable that changes, so in order for me to access my NAS i need a DNS.

I signed up at DynDNS and installed ddClient and it's all working.

What i want is whenever i type in nas.domain.com i get my server. I did a traceroute on nas.domain.com and i can see my ip changing from DynDNS so it should be working.

How do i get my servers ip connected to nas.domain.com?

---

### Post by pqwoerituytrueiwoq on 2012-10-16
Source: [http://dyn.com/support/clients/linux/ddclient/](http://dyn.com/support/clients/linux/ddclient/)
```
# Basic configuration file for ddclient
#
# /etc/ddclient.conf
daemon=600
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=your-username
password=your-password
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
example.dyndns.org
custom=yes, example.com
```this file is located at /etc/ddclient.conf

it appears you are behind a router, most routers have this feature built in, since the router gets the external ip address it can update the account faster and way probe your ip address on a cycle

---

### Post by MortenSJ on 2012-10-16
Thanks for you reply

I use an airport extreme and on DynDNS website they said that i should use a software update.

Do i need to edit anything in the /etc/network/interfaces file?

---

