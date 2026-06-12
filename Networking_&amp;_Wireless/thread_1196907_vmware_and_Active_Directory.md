---
title: "vmware and Active Directory"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by jujitsu-nut on 2009-06-25
Hi folks.

I am using Ubuntu 6.06 on a Dell PE server for Windows patch testing as well as for core application testing. In the past, I had the set up running and it seemed to do what I wanted.

Before I fire it up again I want to make sure my iptables firewall rules will actually restrict the potential communication of Active Directory from our production network.

So here is the basic network config:

Linux/VMWare - eth0 192.168.0.x (able to use production network's router for DNS and updates)

VMNet0 - 192.168.5.x (subnet of testing environment)

Simply put here are my objectives:
[LIST]
[*]Updates are possible - I'd like make sure that Windows servers can get updates (HTTP/HTTPS)and DNS.
[*]The Windows servers cannot 'browse' the production network.
[*]The production network cannot 'browse" the test network.
[*]Neither network can touch the other's Active Directory (udp/tcp 137,138 and 139; TCP 445)
[*]I can use Remote Desktop Connections (TCP 3389) to work on the test servers and workstations as needed.
[/LIST]

I have an iptables custom rules which I have used for this same list of objectives but I am still wondering if I created proper rules.

If anyone is interested in looking into this type of set up let me know and then I will post my rules config.

Thanks.

-james

---

### Post by jujitsu-nut on 2009-06-26
Well I had most of this working the way I wanted before but I just wanted to make sure so I will share some observations. For those that are more experienced with iptables, this may not be of particular interest to you...
[LIST=1]
[*]The default policies for both filter and nat tables are set to DROP.
[*]Necessary traffic to the Linux box is permitted using stateful inspection - only icmp echo and echo reply, ssh and DNS.
[*]Forwarding of packets to nat table is necessary to use PRE and POSTROUTING.
[*]As we use RDP (Terminal Server) connections to a workstation, PREROUTING is used.
[*]Specific web related services are allowed to and from virtual windows boxes - surfing, updates, FTP/FTP data. POSTROUTING is used here.
[/LIST]
Now technically, iptables built-in tables for filter, nat and mangle have predefined port ranges in their default rules. Here's an example using the filter table:
[LIST]
[*]INPUT[0:0]
[*]OUTPUT[0:0]
[/LIST]
To me that means anything above port 0 will blocked. I could be wrong here but I don't believe so. Maybe someone who knows will shed some light on that...

So essentially and wrapping this up, you can do the following:
[LIST=1]
[*]Set you Linux boxen to drop all connections in the filter and nat tables
[*]create appropriate rules for connections only to the Linux boxen
[*]Create forwarding rules to allow the appropriate traffic to and from your Windows boxes
[*]Create the appropriate rules in the nat table to mask as the Linux boxen or convert to target windows ips
[/LIST]
That should be about it.

---

