---
title: "Virtual Network Interfaces?"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by xela321 on 2006-06-24
My school allows me to enter hostname->mac address entries in to the IP management system.  So, I can go to a web page and tell the dhcp and dns servers that when *ff-ff-ff-ff-ff-ff* requests an IP, the dns server will update its entry for *hostname* and point to whatever IP the dhcp server sent to *ff-ff-ff-ff-ff-ff*.

I have registered a few domains to myself and would like my single network card to respond to them.  We'll say hostname1, hostname2, hostname3 are all hostnames that are registered to me.  The only way I can get traffic to those hostnames routed to me is if my network card requests an IP address from that hostname's registered MAC address.

Is this possible?  I'm assuming it is, since vmware on my windows machine uses virtual network interfaces for the virtual machines.  I've look around on the internet for a tutorial, but I can't find anything (maybe I'm not searching for the right terms).

P.S. The IP management system won't allow me to register the same MAC address twice.

---

### Post by xela321 on 2006-07-21
Ok, so after spending some time finishing up projects at work, and taking classes, I was able to tackle this problem again.  I added a dummy ethernet device, dummy0, with 
```
modprobe dummy
```
I ran ifconfig, and it listed dummy0 and showed me it's MAC address.  Now, when I run
```
dhclient dummy0
```
it times out.  When I run dhclient eth0, it works just fine.  Now the trick is, I know I need to bridge the two devices, but I don't know how to without killing my SSH session remotely (which would then require me to walk for a very long time to go fix).

Anyone know how to set up the bridging so I can get this machine to use DHCP?

---

### Post by xela321 on 2006-07-22
When I create a bridge and add eth0 and dummy0 to it, neither device is able to communicate with the network.

Any help?

---

### Post by mips on 2006-07-24
I dunno if I understand you correctly but why not just have a single IP address and your different host names configured in the DNS server with the same IP address ???

You can NOT have multiple IP addresses from the same network/subnet allocated to different interfaces within the same PC/Box/Server etc. What you are trying to do is simply not possible, think about it for a while and you will see why. If you still don't I'll elaborate more.

You could have different addresses for each interface from seperate networks and manually specify a different MAC address for each interface that is different from the physical one. Doing this you would also have to configure secondary addresses on your gateway and enable routing for the new networks. Also have a look at sub interfaces instead of dummies maybe.

---

### Post by xela321 on 2006-07-24
No, what I'm trying to do is create a bunch of dummy ethernet devices, each with their own different MAC address.  I'm thinking that creating a bridge is what I need to do, but for some reason I can't seem to get it to work.  If I create a bridge with dummy0 and eth0, I still get traffic on eth0, but not on dummy0.  However, without bridging, and by setting the IP of dummy0 manually, I can ping dummy0 (static) and eth0 (dhcp).  Setting the IP manually does me no good though, since it won't be in the campus DNS servers (the campus DNS servers are populated with info from the DHCP servers).

---

