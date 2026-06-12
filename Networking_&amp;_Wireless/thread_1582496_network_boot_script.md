---
title: "network boot script"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by max7 on 2010-09-26
ubuntu 10.10 beta

I have setup **/etc/network/interfaces** file 
It sets hwaddress, ip, mask for eth1 and updates iptables
then starts pptp connection

If I type **sudo /etc/init.d/networking restart**
Then it changes mac address, ip address, updates iptables and creates pptp link

internet connection works fine.

But when I reboot it does not work until I type **sudo /etc/init.d/networking restart**

**ifconfig eth1** shows original hwaddress. When I type **sudo /etc/init.d/networking restart** it sets new mac address.


sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults

has not helped.

Could you help, please ?

Thanks,
Max

---

