---
title: "Need to setup my ethernet connection every time I login"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by devashishsethia on 2009-03-25
I recently installed ubuntu 8.10. I need to setup my ethernet connection manually. Everytime the computer starts the ethernet settings are changed to Automatic DHCP and to get my ethernet working I need to manually enter the IP,netmask,gateway etc. each time I log in. Please give me a fix to this problem.
Thanks.

---

### Post by BkkBonanza on 2009-03-25
If you don't want to use dhcp then you need to disable the dhcp client and then manually edit the /etc/network/interfaces file. Once disabled the dhcp client won't keep rewriting that file for you.

Depends on your dhcp client but it may be,

/etc/init.d/dhclient stop

and if I recall correctly,

update-rc.d dhclient stop

so that it doesn't do it on boot. Now I guess you know how to set the interfaces since you have been doing that each time. Enter that info into the file above. See,

man interfaces

---

### Post by chili555 on 2009-03-25
I suggest you amend */etc/network/interfaces* file like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
```Substitute your details as necessary. If Network Manager is installed, I would remove it in Synaptic. Reboot and enjoy.

---

