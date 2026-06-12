---
title: "Fixed my wired ethernet after wicd install"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by xxxYYY on 2010-08-16
I hope it sticks.  Anyway, after I installed wicd on someone's recommendation (the default network manager GUI did not seem to connect to hidden wireless networks but could connect to open ones)  which deleted the other network manager, neither my wireless would work at all nor my ethernet.

sudo dhclient eth0 gave an error, it expected /etc/resolv.conf to be a symbolic link.
  
After the following, my ethernet works at least.  Haven't tried wireless, nor have I rebooted since the fix:

	cd /etc
	sudo mv resolv.conf resolv.conf.save
	sudo ifdown eth0
	sudo /etc/init.d/networking restart
	ln -s resolvconf/run/resolv.conf
	sudo ln -s resolvconf/run/resolv.conf
	sudo dhclient eth0
	ping [www.google.com](www.google.com) (now works)

---

