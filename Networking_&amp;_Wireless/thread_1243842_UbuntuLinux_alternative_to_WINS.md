---
title: "Ubuntu/Linux alternative to WINS"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by HDave on 2009-08-18
I have a network with a bunch (two dozen+) Ubuntu machines on it -- most of which use DHCP to get an IP address.

I would like to have each machine use the hostname of other machines for file sharing, ssh, etc., etc.

What is the best way to resolve host names of DHCP Ubuntu computers on a network?  DNS doesn't work with DHCP hosts.  I know I can do it with Samba/WINS, but there has to be a better way....

---

### Post by HDave on 2009-08-19
I think I found it:  dnsmasq

---

### Post by HDave on 2009-08-19
Also it turns out you can get dhcp to dynamically update dns:

[http://www.debian-administration.org/articles/255]("http://www.debian-administration.org/articles/255")

---

