---
title: "/etc/hostname multiple hosts?"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by spezticle on 2011-01-04
is it possible to set eth1 to be hostnameexample1 and eth0 to be hostnameexample2?

---

### Post by Brandon Williams on 2011-01-05
It would be easier if you would explain what you're trying to accomplish by doing this. /etc/hostname provides the primary hostname of your machine, but it doesn't have anything to do with actual name resolution. If you want to be able to use different hostnames to access the IP address assigned to eth0 and the IP address assigned to eth1, you can do that by adding entries to your /etc/hosts file for the hostname/address pairs. This will only impact local name resolution, though, and it won't help remote machines to access your machine more easily. If you want remote machines to be able to connect to this machine with a different hostname for each interface, you'll have to add the necessary entries to your DNS server. The method for doing so will depend upon the type of DNS server you're using.

---

