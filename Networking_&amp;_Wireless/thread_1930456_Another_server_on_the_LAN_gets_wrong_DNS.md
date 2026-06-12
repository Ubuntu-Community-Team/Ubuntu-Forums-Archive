---
title: "Another server on the LAN gets wrong DNS"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-02-23
Hi,

We have a 2nd server on our LAN: server2.mydomain.com

When some users try to map a drive to server2 the are directed to our WAN IP instead of the local (192.168.x.x) IP.

The DNS server is at opendns.com.  IP addresses:  208.67.222.222 and 208.67.220.220.  All internet traffic goes through server1 (the main server) and all LAN users point there DNS to server1 via server1's DHCP server.

I want users to find server2 locally.  IOW I want DNS requests to server1 for server2 to refer to the 192.168.x.x address.

Can this be done with an entry in server1's /etc/hosts file?

Thanks,

AB

---

