---
title: "Multipul Vlans with NIC in server 12.04"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by ataylor1988 on 2013-05-10
I am setting up a 12.04 server to be a DHCP server for our network.  I am trying to setup vlans 2-12 on this box.
I have been following this thread
[http://ubuntuforums.org/showthread.php?t=1465860&page=3](http://ubuntuforums.org/showthread.php?t=1465860&page=3)
Mostly the instructions in the second to last post.

I get my /etc/network/interfaces file setup like the example in that post.
I plug it into a vlan trunk port on my cisco switch. which has all the vlans going through that trunk.  I can watch the vlan interfaces come up on the cisco through console, but i cannot ping the router, and the router cannot ping it.

Is there a better way to setup virtual nics for vlans than those instructions or am i do something wrong?  Once i get simple communications working I will then work on getting the DHCP server working

---

### Post by ataylor1988 on 2013-05-14
Bump?

Anyone i could really use some help with this?

---

