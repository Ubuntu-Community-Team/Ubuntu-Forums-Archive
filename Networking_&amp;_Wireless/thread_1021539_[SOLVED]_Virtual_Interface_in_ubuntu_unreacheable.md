---
title: "[SOLVED] Virtual Interface in ubuntu unreacheable"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by fouadatmeh on 2008-12-25
Hello,

I have a router simulator (GNS3) installed on Ubuntu 8.10.
I have created a virtual router (running on the Ubuntu host PC) and connected it to my LAN via eth0 and I can ping both ways between the router and other PC's on the LAN (the router having its own IP address)
The problem is I cannot ping between the host PC and the router running inside it. and this seems to also cause a problem when I try to open an HTTP session with the router from the LAN. (btw: I can open sessions **from the LAN** with other virtual routers that are behind the first one connected to eth0)
I haven't installed any firewalls and the ufw is "not loaded"..

What could be causing the problem as I have the same thing on windows and it worked there :(
Thank you in advance for any tips and please don't hesitate to as for any more clarification.

---

### Post by fouadatmeh on 2008-12-27
Hello Guys,

Any help or suggestions please...?

---

### Post by fouadatmeh on 2008-12-27
I FOUND IT :)

I needed to create a tap interface, create a bridge between the tap and eth0 and then connect the virtual router to the tap interface.

for the details go to:
[http://www.blindhog.net/linux-bridging-for-gns3-lan-communications/#comment-21398](http://www.blindhog.net/linux-bridging-for-gns3-lan-communications/#comment-21398)

Regards,
Fouad

---

