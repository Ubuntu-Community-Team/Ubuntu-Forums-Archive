---
title: "Network issue after removed network-manager"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by Du, Wei on 2012-03-25
Hello,
 
I'm working on Ubuntu since 8.04. 
 
We have NIS environment here, so every time after I installed a new version, I removed Network-Manager and configure eth0 manually. Because Network-Manager will overwrite my customed network configuration files automatically.
 
But this time after I removed network-manager from Ubuntu 11.10, and configured /etc/network/interfaces as following:
 
# apt-get remove network-manager network-manager-gnome
 
# nano /etc/network/interfaces 
 
add the following:
 
auto eth0
iface eth0 inet dhcp
 
add then restart the neworking service as following:
 
# /etc/init.d/networking restart
 
I get this:
 
* Running /etc/init.d/networking restart is deprecated because it may not again enable some interfaces
* Reconfiguring networking interfaces
RTNETLINK answers: File exists
 
I don't know what happened on Ubuntu 11.10, this has never happend before on the previous versions.
 
Any suggestion is much appreciated.

---

### Post by papibe on 2012-03-26
Hi Du, Wei.

I've seen that error when trying to add a network route that already exists. Then, it may be just a warning. Did you get the rest working (ip assigned, network access, etc)?

Also, if there are confusing routes a simply reboot can fix it.

Hope that helps, and tell us how it goes.
Regards.

---

