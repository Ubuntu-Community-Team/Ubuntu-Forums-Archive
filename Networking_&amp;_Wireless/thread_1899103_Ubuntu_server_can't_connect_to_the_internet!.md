---
title: "Ubuntu server can't connect to the internet!"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by slugiscool99 on 2011-12-22
Please help! I have recently started an ubuntu 11.10 server but none of the apt-get or updates work because I cannot connect to the internet! There is no resolv.conf file, and the DHCP setup didn't work in the installation process. (I selected to install later) PLEASE HELP!!!! Thanks :D

---

### Post by chili555 on 2011-12-23
Wired or wireless? Is there a working driver? Please post:```
sudo lshw -C network
```Are you connected to a router? What is a sample IP and gateway address from another computer on the same network?

---

