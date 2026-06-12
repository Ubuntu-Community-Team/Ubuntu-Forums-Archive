---
title: "Where are the backport modules for wireless?"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by angelsguitar on 2011-10-14
Hi.

There used to be a package called linux-backport-modules-wireless-* but I can't find it on 11.10's repos. Is it still included? Did the name changed?

I need that package in order for my wireless to work properly.

---

### Post by angelsguitar on 2011-10-15
Although I still haven't found the backported modules, the following solution worked for me:

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal)

Basically, these are the instructions:

> 
1- First method : You need to disactivate IPv6, to do that, open terminal and enter the following commands:

echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

Then restart your system.

If you still have the issue, follow also instructions on step 2.

2- Second method:  A second solution for this issue can be by using the following :

Open terminal and enter the following command:

sudo -s
gksu gedit /etc/modprobe.d/ath9k.conf

at the end of the file add this:

options ath9k nohwcrypt=1

Save an restart your OS.


Hope this helps someone.

---

