---
title: "Two ethernet cards in Ubuntu Server"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by h.juan01 on 2009-05-16
[B]I have to Ethernet cards in my server. One integrated in the MB and the other PCI. 
How can I do to configure them? I want eth0 for LAN conection and eth1 for INTERNET conection. How can I do it?

Please help!

[/B]

---

### Post by Adina on 2009-05-16
maybe this is what you are looking for.

[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

---

### Post by h.juan01 on 2009-05-16
That's not what i'm lookinf for. I have a router and 3 access points so i do not need that. i want to separate the conections. I want the server to obtain internet conection by eth0 and to have access to the local network by eth1. Both eth0 and eth1 are conected to the same router.

---

### Post by uupreti on 2009-05-16
How many computers you have and how many routers? If you want to separate network then you might have to separate subnet. Can you elaborate your problem more clearly??

---

### Post by h.juan01 on 2009-05-16
I want one network adapter to do all the internet trafic and no trafic which will work with an ftp server. And i want the other network adapter to do all the local network trafic which will use a samba files server

---

### Post by uupreti on 2009-05-16
So you might want to separate your network physically. If you want to separate logically then I will suggest you using different subnet. You will get one ip from your router (DHCP) server and static for other network.

Connect eth0 to internet router and eth1 to different switch or router which will give different ip address pool.

---

### Post by h.juan01 on 2009-05-16
As i cannot do waht i want i wont do it.

I wanna know if i can make work both network adapters in the same network, so if one of them failed, i would still have internet in the server. I mean something similar to RAID 1 in hard drives but made with network adapters. And i read also that if you have two network adapter you avoid the data transfer bottleneck
Is that possible?

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

