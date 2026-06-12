---
title: "Internet Connection Issue (netroot works, normal boot doesnt)"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Progressive on 2010-07-15
After my upgrade to maverick, I have been unable to connect to the internet normally. "ifconfig -a" shows that my standard integrated intel ethernet slots are detected. Using "sudo /etc/init.d/networking Restart" does nothing.

However, if I use recovery mode and select the "netroot" option, I am able to get a connection. Then I can startx and be up and running.

What does the netroot option do differently, and how can I script it to execute automatically?

---

### Post by Progressive on 2010-07-15
ok I think I fixed it.

Just needed to modify my /etc/network/interfaces

and added the following lines:

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

---

### Post by dino99 on 2010-07-16
this have happened to me today: 

eth0 activated but cant update packages or use browser
need to deactivate eth0 (icon) then reactivate it to be really connected

---

