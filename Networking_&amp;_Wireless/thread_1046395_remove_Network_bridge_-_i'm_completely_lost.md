---
title: "remove Network bridge - i'm completely lost"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by liniaal on 2009-01-21
ive been wanting to link my virtual machines in virtualbox connected to the internet, using them as servers. lately, in all despair trying to port forward host's 8080 to guest's 80, 2222=>22 etc, i decided to get re-acquainted with network bridges. situation right now is that br0 is not removeable, causing my real nic, which i for ease of reading will call eth0, somehow to not get through to outside. when i get back home, i'll post stuff like /etc/networking/interfaces e.a.
how can i remove the br0, or disconnect eth0 somehow from it - how can i get *back* to normal operation?

ps the command ```
sudo /etc/init.d/networking restart
``` gives a warning about some /var/run/dhclient*.pid already exists.

---

### Post by liniaal on 2009-01-21
so, first i tried the VBoxManage command to port forward, and after that, i followed the howto on [www.ubuntugeek.com/how-to-set-up-host-interface-networking-for-virtualbox-on-ubuntu.html](www.ubuntugeek.com/how-to-set-up-host-interface-networking-for-virtualbox-on-ubuntu.html) .
i really really want to go back to trying the port forwarding (and of course to having internet connection on my main machine again)

---

### Post by liniaal on 2009-01-22
ok, i fixed it, by rebooting :).
it appears some settings of /etc/network/interfaces do not get taken into account when does a /etc/init.d/networking restart (if NetworkManager is running?). however - i'm super glad it worked right out of the reboot because if it wouldn't, i would've had a problem.

greetings yall

---

### Post by ramilehti on 2012-06-20
You can also use 

brctl delbr <insert bridge interface name>

So you don't have to reboot.

---

