---
title: "Virtual Network Interfaces help"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by PhrankDaChickenGeek on 2010-08-24
I am trying to set up two virtual network interfaces on Ubuntu server 10.04.

I want to be able to have 2 hostnames resolve to my machine on my school's network. So both interfaces must be dhcp.

I want this so I can run 2 websites on different hostnams, ie, [http://myweb1.myschool.edu](http://myweb1.myschool.edu) & [http://myeweb2.myschool.edu](http://myeweb2.myschool.edu).

I can change the name of my website by configuring /etc/dhcp3/dhclient.conf, but I wouldn't know how to do it with virutal interfaces.

How do I setup virtual/mapping interfaces in /etc/interfaces/networking?
How do I send my desired hostname to the dhcp server for both interfaces?

thanks.

---

### Post by Iowan on 2010-08-24
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a link I've had bookmarked for awhile - hope it's still useful...

---

### Post by PhrankDaChickenGeek on 2010-08-25
> **Iowan said:**
> [Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a link I've had bookmarked for awhile - hope it's still useful...

Not really what I'm looking for - I'd need a static ip address for that - I get mine from a dhcp server which I do not administer.

I need it to look like I have two separate machines attached to the network to get it to work, so I can send the dhcp/dns server my desired hostname.

---

