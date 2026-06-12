---
title: "How to secure RDP to prevent unauthorized access"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by tvbowman on 2013-02-08
I am using XRDP to connect from Windows to my Ubuntu 12.10 machine. I have adjusted the hosts.allow and hosts.deny files according to the instructions I found, but still anyone with a network username can access the box from any IP address. I would like to secure the connection in one of the following ways:

1. Restrict RDP to only allow connections from 10.1.x.x or 10.11.x.x addresses, OR

2. Restrict access on the Ubuntu machine to only users located in the 'Administrators' group (if there is one.)

---

### Post by tvbowman on 2013-02-08
More info, if needed:

in hosts.allow, I have the following:

ALL: 10.1.
ALL: 10.11.


and in hosts.deny, I have the following:

ALL: ALL

---

### Post by steeldriver on 2013-02-08
well I'm not sure if it's the best way, but you could set up a firewall rule (via iptables or ufw) e.g. to allow RDP to from any hosts on my LAN I have ufw rules

```

3389                       ALLOW       192.168.1.0/24
3350                       ALLOW       192.168.1.0/24

```Port 3389 is the default port for RDP itself, and 3350 is used by sesman.

---

### Post by tvbowman on 2013-02-08
> **steeldriver said:**
> well I'm not sure if it's the best way, but you could set up a firewall rule (via iptables or ufw) e.g. to allow RDP to from any hosts on my LAN I have ufw rules

```

3389                       ALLOW       192.168.1.0/24
3350                       ALLOW       192.168.1.0/24

```Port 3389 is the default port for RDP itself, and 3350 is used by sesman.

Can you tell me where to do something like this? My LAN firewall only restricts communications between our LAN and the outside, it does not restrict LAN to LAN communications. I would need a firewall on the Ubuntu machine?

---

