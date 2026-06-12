---
title: "router https"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by Mosabama on 2010-12-17
Hi,

I have a D-link router that while working suddenly stops https traffic. I have to restart it to enable https again. nothing goes wrong with any other protocol like http, ssh or any other.

Router: D-Link DSL-2640U
Machines: 1 windows 7 and my laptop (ubuntu 10.10).

I get this when running snmp:

```
Starting Nmap 5.21 ( http://nmap.org ) at 2010-12-18 03:33 EET
Nmap scan report for 192.168.1.1
Host is up (0.019s latency).
Not shown: 994 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
23/tcp   open     telnet
80/tcp   open     http
443/tcp  filtered https
5431/tcp open     park-agent

```

what does this filter mean next to https ?
I reset the router before and configured it again, but nothing changed.

if I restart the router it will enable https and after a couple of minutes it disables it for some reason.
Thanks in advance.

---

### Post by gmargo on 2010-12-18
From the **nmap(1)** man page (or online at [http://nmap.org/book/man.html):]("http://nmap.org/book/man.html%29:")
> 
Filtered means that a firewall, filter, or other network obstacle is blocking 
the port so that Nmap cannot tell whether it is open or closed.


---

### Post by Mosabama on 2010-12-18
indeed !! what maybe blocking the port?

---

### Post by Mosabama on 2010-12-18
```

> iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             192.168.1.1         udp dpt:domain to:195.175.39.40 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:ssh to:192.168.1.2 
DNAT       udp  --  anywhere             anywhere            udp dpt:ssh to:192.168.1.2 
DNAT       all  --  anywhere             anywhere            to:192.168.1.2 
REDIRECT   udp  --  anywhere             anywhere            udp dpt:5060 redir ports 5060 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:https to:192.168.1.3:443 
DNAT       udp  --  anywhere             anywhere            udp dpt:https to:192.168.1.3:443 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:37674 to:192.168.1.3:37674 
DNAT       udp  --  anywhere             anywhere            udp dpt:37674 to:192.168.1.3:37674 
DNAT       udp  --  anywhere             anywhere            udp dpt:37675 to:192.168.1.3:37675 
DNAT       udp  --  anywhere             anywhere            udp dpt:46209 to:192.168.1.3:46209 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:46209 to:192.168.1.3:46209 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:26997 to:192.168.1.3:26997 
DNAT       udp  --  anywhere             anywhere            udp dpt:26997 to:192.168.1.3:26997 
DNAT       udp  --  anywhere             anywhere            udp dpt:60297 to:192.168.1.2:60297 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:60297 to:192.168.1.2:60297 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:51413 to:192.168.1.2:51413 

```

This is the Nat table of iptables in the router.
Edit:
and for the record I didnt play with these settings and the https here seems fine, does it?

---

### Post by Mosabama on 2010-12-20
up

---

### Post by Mosabama on 2011-01-04
Anyone?

---

