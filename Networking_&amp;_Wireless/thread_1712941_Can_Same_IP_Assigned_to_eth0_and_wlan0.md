---
title: "Can Same IP Assigned to eth0 and wlan0?"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by helpee on 2011-03-23
Hi,

I'm running Ubuntu Server 10.10 on a 64 bit laptop (also have GNOME installed just for convenience), and have a website up using apache2. I am wondering if it is possible to configure both eth0 and wlan0 to the same local static IP address?  I would like to walk around my house and do stuff when I want and still have the website accessible, but also be able to jack my laptop back into the router when I am away, just for peace of mind.

Is this possible? If it is, do I need to do some configuring in apache2 to tell it to use another device? Is this even a smart way to get what I want done? Any help is greatly appreciated!

---

### Post by helpee on 2011-03-25
bump?

---

### Post by Cheesehead on 2011-03-25
You want to create a **bridge** between the two interfaces.

Great tutorial at [http://wiki.debian.org/BridgeNetworkConnections](http://wiki.debian.org/BridgeNetworkConnections)

---

