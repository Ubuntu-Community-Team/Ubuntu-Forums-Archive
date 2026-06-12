---
title: "New Server with Netgear WGT624"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by andrewqsmith on 2011-03-05
Installed a Ubuntu Linux server and have setup up many features on it. Shorewall has been installed and exceptions have been added to allow HTTP and SSH. When using another computer I can obviously access the server webpages and even the webmin I installed. Unfortunately I am no router expert and do not know what to do with this model of router in order to get the public IP accessible to the world wide web. I am in desperate need of help to figure out this last crucial step. I have looked at the router setting and have tried messing with the port forwarding and the static routes and haven't had much luck. Typically I can figure this stuff out but I don't want to spend a week pulling hair on something that is probably really simple but I just don't know. Any help is greatly appreciated.

---

### Post by prshah on 2011-03-05
> **andrewqsmith said:**
> I have looked at the router setting and have tried messing with the port forwarding and the static routes and haven't had much luck.

You can look at the relevant pages for your router in [portforward.com]("http://portforward.com/english/routers/port_forwarding/Netgear/WGT624/SSH.htm") (note that there are multiple types of routers for this model, so choose the appropriate model).

If you are running a server, and are confident about your server security, you can do away with the extra security of your router's firewall / NAT, and setup the router's DMZ to point to your server's internal IP.

---

### Post by andrewqsmith on 2011-03-05
Thanks for your advice. I had done many of these steps yet could not get public access. I finally relized the problem is with my ISP blocking port 80. I am using cox communications. DO you have any suggestions on what I can do from here?
 
Thanks

---

