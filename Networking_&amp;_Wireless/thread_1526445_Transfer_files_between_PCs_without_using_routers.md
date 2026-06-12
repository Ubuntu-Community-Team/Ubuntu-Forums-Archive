---
title: "Transfer files between PCs without using routers"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by gotokhaleel on 2010-07-08
Hi
I have 2 laptops and 1 PC at home running Ubuntu. All these are connected to a wireless router for the internet usage. 
When I try to copy a file from a shared folder of other laptop, the whole of data passes through the router. 
This affects the internet bandwidth within the network. 
Is there a way to access the shared files without necessarily going through the router and also without affecting the internet connectivity.

---

### Post by teejaybee on 2010-07-08
Rate limit the transfer, either in the router or on the machine itself with iptables. You could do this either by port (eg. samba, ssh, etc) or between the two IP addresses.

---

