---
title: "Ubuntu Client Windows DNS Server Issue"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by neosar on 2009-09-24
Hi,

I am in a corporate network that uses Windows for our DNS server, and am having some trouble pinging an ubuntu host from a windows workstation.  Here's the situation as of now.  I have Ubuntu Server 9.04, and I've configured /etc/resolv.conf as well as /etc/dhcp3/dhclient.conf both to point to our internal primary and secondary DNS servers.  When on my Windows workstation I get no hostname resolution when I attempt to ping my Ubuntu box by hostname.  I also get no result when doing an nslookup on my Ubuntu hostname.  However, if I do an nslookup on the IP address of my Ubuntu box it returns the correct hostname.  Am I missing a step here that registers DNS both ways?

Thanks,

Mike

---

### Post by doas777 on 2009-09-24
the problem is likely as you mentioned DHCP DDNS registeration. I don;t have any good advice but to look into samba for getting it done. all the guides I find on the topic assume you have a ubuntu server and windows clients.

---

