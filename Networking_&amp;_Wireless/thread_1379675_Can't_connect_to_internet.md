---
title: "Can't connect to internet"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by jimmy.eric on 2010-01-12
Well, I was trying to open a port for SSH and managed to mess everything up.  

I have ubuntu server with two NIC's.  One NIC for DSL and the other for DHCP.

Both were working correctly until I installed firestarter.

Now I can get on the Internet with computers connected to the server but I have no Internet on the server itself.  

I still get an IP Address on eth0 (dsl0) and I can still ping Google's DNS from the terminal but I can't ping google.com or anything.

Anyone have any ideas what I can do to determine what my problem is?

---

### Post by jimmy.eric on 2010-01-12
I just found out that I can ping IP Addresses just not host names.  So that would mean there is a problem with my DNS right?  How come my computer seems to be able to give other computers via DHCPD the correct DNS server addresses but it can't get it right on the server?

---

### Post by Iowan on 2010-01-12
It does sound like DNS problem. What is in */etc/resolv.conf* for the server itself?  It doesn't necessarily have the same information it feeds to it's DHCP clients.

---

### Post by jimmy.eric on 2010-01-13
/etc/resolv.conf wasn't even there anymore.  So I recreated it and everything works now.  Thanks!  Not sure how I managed to delete it though.

---

