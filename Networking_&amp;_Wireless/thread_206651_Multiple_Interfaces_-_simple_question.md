---
title: "Multiple Interfaces - simple question"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by mem on 2006-06-30
Hey,
I've got a multi-interface machine here that I've had setup with one connection for the past two weeks. I just pluged in its second interface and want all traffic going to the 192.168.1.0 network to travel through that interface, rather than the internet connection. I think this means i need to use IPtables, but i have no idea where to begin.

EDIT: think i just figured it out... 'route'. when i pluged in the second interface, it created a new 'default' route entry. is there anyway i can stop this from happning in the future?

Any help would be greatly appreciated.

---

### Post by ohgod on 2006-06-30
IPtables doesn't do routing as far as I know.  What you really need to do is modify the kernel's routing table.  Check out the route command:  [http://linux-ip.net/html/routing-intro.html](http://linux-ip.net/html/routing-intro.html)

---

### Post by mem on 2006-06-30
yea, when i walked over to the machine and did 'route', it came up with **two** 'default' routes; one for each interface. Is there a way to stop it from adding the 'default' entries in the route table when the interface comes up?

---

