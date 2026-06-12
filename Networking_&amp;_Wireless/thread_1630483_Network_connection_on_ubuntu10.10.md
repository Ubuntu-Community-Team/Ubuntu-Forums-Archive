---
title: "Network connection on ubuntu10.10"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by samorn on 2010-11-25
Hi i face a problem with network connection on ubuntu10.10 (ethernet , wlan , broadband). 
the problem is i can't switch the connection by easy way like i ever do with old version of the ubuntu10.04.
i have check the solution on internet ask to the commend bellow:
sudo vi /etc/network/interfaces
Example:

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.14
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.30
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.30

save after edit the text
sudo /etc/ini.t/networking restart
then it work.

but went i change the ip in connection manager on graphic to 192.168.0.16
then i type commend ifconfig
it still show the old setting was set by comment.
for wlan i didn't how to get it work.

I have already in latest version of kernel 2.6.35-23-generic x86_64
please help...

---

