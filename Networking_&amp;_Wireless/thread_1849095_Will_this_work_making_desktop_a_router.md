---
title: "Will this work? making desktop a router"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2011-09-23
assuming this will work

i want to make the desktop work as a router and allow my laptop to connect to the Internet the (desktop only has one Ethernet port)

pleases not the attachment
edit:
worked:
i put this in my rc.local file
ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -P FORWARD ACCEPT
service dhcp3-server start

---

### Post by Iowan on 2011-09-23
Your drawing looks like my network ( My modem is a DSL modem). My modem also has some router features - most of which are turned off. I DO have another machine acting as DHCP/DNS server, but it wouldn't be absolutely necessary if I opted for static addresses. I'll need to check my other machine for links about connection sharing. Is your modem a stand-alone device with an IP address?

---

### Post by pqwoerituytrueiwoq on 2011-09-24
the modem supports 34 address but it gives them in bridged mode all it gives you is a status info there are no editable settings
the dsl modem i have seen are also routers
this thing only gives local network address if there is no Internet service

---

