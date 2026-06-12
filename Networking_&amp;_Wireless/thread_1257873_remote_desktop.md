---
title: "remote desktop"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Hogosha on 2009-09-04
I use remote desktop a lot on my  networks and for some reason i cannot use computer names in Ubuntu, i have to use ip address. Is there something i am missing or is this a standard for ubuntu?

---

### Post by superprash2003 on 2009-09-04
in your terminal type **ping hostname** where hostname is the name of the computer.. what does it output?are these static ips?

---

### Post by Grenage on 2009-09-04
Check your /etc/reslve.conf, it should list DNS servers and often a search domain.

---

### Post by Hogosha on 2009-09-04
with the ping i get unknown host **hostname**

with the resolv.conf i get a name server, but i still get no resolution

---

### Post by doas777 on 2009-09-04
ok, it sounds like you have not set up name resolution for your internal networks. you will prolly need to do one of the following:


[LIST=1]
[*]create a hosts file for each pc that contains the names and ips of your hosts and place it on each host that needs to resolve.
[*]create a DNS or WINS server for your network and point your clients to it for naming res. then if the query is unresolved, forward it onto a public DNS server.
[/LIST]

---

### Post by Hogosha on 2009-09-04
we used to have a DNS server for the place but we changed the set up and we are now letting a router handle that and DHCP. We also switched to everything but the servers to DHCP.

---

### Post by doas777 on 2009-09-04
> **Hogosha said:**
> we used to have a DNS server for the place but we changed the set up and we are now letting a router handle that and DHCP. We also switched to everything but the servers to DHCP.


well unless your doing DDNS, your DHCP server will only be passing out the IP of your DNS server to clients. are your clients now pointing to the router, and if so, is the router configured with your zone information?

---

### Post by Hogosha on 2009-09-04
yes, everything is pointing to the router, i am note sure if the zone info is set. I cannot check right now because i am on campus, but even on campus i cannot use the host names.

---

