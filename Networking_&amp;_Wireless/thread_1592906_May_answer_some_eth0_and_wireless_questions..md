---
title: "May answer some eth0 and wireless questions."
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by wnelson on 2010-10-11
The following may help some with network connection problems. I also provide a short cut. It also provides a way to turn off ip6.

As root edit    /etc/netowrk/interface    the following can be done to setup eth0/? without using the network manager.

Dynamic/DHCP address

auto eth0
    iface eth0 inet dhcp

Static Address

iface eth0 inet static
    address 192.168.0.7
    netmask 255.255.255.0
    gateway 192.168.0.254

While logged in as root. You can

cd /etc/init.d
./networking restart

This restarts your networking without rebooting

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Debian way of setting up wireless networking.

[http://wiki.debian.org/WiFi/HowToUse](http://wiki.debian.org/WiFi/HowToUse)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are many ways to turn off the IP6 protocol. This is the simplest for me.
As root.
edit   /etc/sysctl.conf    add the following.
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Then when you reboot you can see IP6 is turned off.

Walt

---

