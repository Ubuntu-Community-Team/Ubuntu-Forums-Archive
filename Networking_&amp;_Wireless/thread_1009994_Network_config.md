---
title: "Network config"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by ExemplarUbuntu on 2008-12-13
Having updated to Ibex and (for once) the network wasn't broken, I was
surprised to find that my home config is missing. The office one
still works.
I am trying to set it up again but they have changed the config tool
and it's not as clear as the last one.
I can ping my router (fixed ip) but cannot see it with Firefox
nor can I DNS to anything.
I have entered the ip address, netmask 255.255.255.0 and gateway
ip of my router as before.
Any ideas ?

---

### Post by iponeverything on 2008-12-13
If your /etc/resolv.conf is does not contain nameservers add the opendns servers:

```
nameserver 208.67.222.222 
nameserver 208.67.220.220

```

---

### Post by dragos_iliescu_2005 on 2008-12-13
Looks like firewall block connection to Internet.

---

### Post by ExemplarUbuntu on 2008-12-13
The Atari connected to the router works fine so I
doubt it is a firewall issue.
.
I managed to manually edit the interfaces file and I
can now browse to the webpage of the router. So it now
just looks like a DNS problem.
.
The new config does not show up in the configuration tool.

---

### Post by superprash2003 on 2008-12-13
presuming its solved.. please mark thread as SOVLED

---

### Post by ExemplarUbuntu on 2008-12-13
I added the adsl router ip to resolv.conf and I am now
able to connect.
.
The config tool is fairly useless. At least the Heron one
worked.
.

---

