---
title: "Static route disappears"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by umitclaw on 2009-04-28
A static route has disappeared on my mail-relay server several times.  I am in the midst of moving machines from one DMZ to another, both of which have the same subnet.  I have moved my Hardy mail-relay to the new DMZ, while my old RH9 web-server remains in the old DMZ.

Example (IPs changed):
{OLD DMZ

Old Firewall INT IP: 192.168.1.1/24, DMZ IP: 10.10.1.1/24
ip route add 10.10.1.25 via 192.168.1.2

RH9 Web-server IP: 10.10.1.80
default routing:
dest        gateway   genmask      device
10.10.1.0  0.0.0.0     255.255.255.0 eth0
0.0.0.0    10.10.1..1   0.0.0.0         eth0
route added:
ip route add 10.10.1.25 via 10.10.1.1
}

{NEW DMZ
New Firewall INT IP: 192.168.1.2/24, DMZ IP: 10.10.1.1/24
ip route add 10.10.1.80 via 192.168.1.1

Hardy Mail-Relay IP: 10.10.1.25
default routing:
dest        gateway   genmask      device
10.10.1.0  0.0.0.0     255.255.255.0 eth0
0.0.0.0    10.10.1..1   0.0.0.0         eth0
route added:
***ip route add 10.10.1.80 via 10.10.1.1***
}

By adding these routes, my web-server is able to connect to the mail-relay.   However, the static route on the mail-relay (denoted by ***) randomly disappears every couple of days.  

Does anyone know why this is happening?  Is there something in Hardy that would clear out this route because it is to an address within the local subnet?

---

