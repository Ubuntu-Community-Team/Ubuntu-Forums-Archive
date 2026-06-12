---
title: "Help with DHCP and DNS"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2009-05-06
I'm helping a Boys and Girls Club set up a server for their network and I've only walked into places with a DNS server already set up.

They have a CISCO firewall that is currently handling their DHCP requests, two routers and a mess of PC's - the routers basically separate the staff computers from the lab computers.

I'm going to install Ubuntu server along with Samba, Amanda and would like to use names instead of static IP's - or is it better to have servers with static IP's?  They currently do not use it as an external web server.

Any pointers gratefully appreciated

---

### Post by bhaverkamp on 2009-05-06
A base ubuntu install incude the open source version of bonjour. Even with DHCP this allows you to refer to other computers on your network by name. Just tack a '.local' onto the names of the computers you want to refer to....

---

### Post by matthewboh on 2009-05-06
What's the name of it and does it work with windows?

---

