---
title: "Ics through router"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by MajorTom00 on 2009-03-28
I've been all over these forums and google, and still don't really know how to do this. 

I've got an Ubuntu server with dhcp and isp enabled, could anyone tell me how to route that signal through a hub or router (whos dhcp is off)?

---

### Post by netztier on 2009-03-28
> **MajorTom00 said:**
> I've been all over these forums and google, and still don't really know how to do this. 

I've got an Ubuntu server with dhcp and isp enabled, could anyone tell me how to route that signal through a hub or router (whos dhcp is off)?

>parse error during question interpretation<

Can you be more detailed?

Are we talking multiple NICs (Network Interface Card), multiple LANs? Ubuntu machine with one NIC to the local LAN, the other to the outside LAN? 

Who offers DHCP service on which of these LANs? Are there any "private addresses" involved as per RFC1918 (192.168.x.x, 172.16-31.x.x, 10.x.x.x)? Are there any other addresses configured on that Ubuntu Server?

Can you show the outputs of these commands?

[LIST]
[*]netstat -nr
[*]ifconfig -a
[*]cat /etc/network/interfaces
[/LIST]

regards

Marc

---

### Post by superprash2003 on 2009-03-28
disable DHCP in your wifi router and setup dhcp server in ubuntu. This tutorial should help [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html)

---

### Post by MajorTom00 on 2009-03-28
Thanks for the response.

Yes, of course there are multiple NIC's, eth0 is connected to a gateway router, eth1 is the NIC to be used for the internal network. 

eth1 has dhcp and internet connection sharing enabled, this connection works fine when a single computer is connected with a flip cable. I've tried connecting this nic, using a flip cable to the wan port on a router who's dhcp is disabled, but no computers who connect to that router can get IP addresses.

I guess that's where my problem is.

---

### Post by MajorTom00 on 2009-04-04
**Bump**

Well, I solved this problem on my own, and it was crazy easy to solve. In my original question, I simply ask how to set up a router as a hub to share an internet connection from a linux server to several clients. This is assuming that dhcp and ics are working properly (and they were).

I found this guide to be most helpful:
[http://www.broofa.com/blog/2007/03/using-a-router-as-a-hub/]("http://www.broofa.com/blog/2007/03/using-a-router-as-a-hub/")

---

