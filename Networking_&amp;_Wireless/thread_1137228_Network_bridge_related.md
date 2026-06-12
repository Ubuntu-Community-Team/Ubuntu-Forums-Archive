---
title: "Network bridge related"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by whatis tux on 2009-04-25
Hello,

I've installed VirtualBox 2.2 on Ubuntu 9.04 and I've set the virtual machine (Windows XP) to use Host-only Network instead of NAT (which works fine, but i dont want it) and I want to create a bridge between my Laptop's (which is behind a router) wireless interface (wlan0) and virtualbox's interface (vboxnet0).
Since this is the first time I'm doing this, i have some problems/questions which I hope you guys can clear them out for me.

I've installed 'uml-utilities' and 'bridge-utils' via apt-get and I did these steps in order to create a temporary bridge to test things out :

brctl addbr br0
brctl addif br0 wlan0 vboxnet0
dhclient br0 

I don't know if the bridge (I imagine it as a virtual interface with no ip) should have an ip but I saw others assigning one to it so.. anyway and I don't know either if the ip for the host/guest vboxnet0 interface should be in the same subnet as the ip from host's wlan0 interface (which is 192.168.1.3) something like 192.168.1.x (I don't see how a machine could have two interfaces with the same ip (I'm reffering to the host)). I've tried this way and it doesn't work.

The picture attached describes better what I want, only that my laptop has Ubuntu as host and Windows as guest. So how should I proceed?

Thanks...

---

