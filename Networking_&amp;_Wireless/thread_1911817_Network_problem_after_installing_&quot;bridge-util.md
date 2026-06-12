---
title: "Network problem after installing &quot;bridge-utils&quot;"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by danielsender on 2012-01-19
Hi,

In my ubuntu 11.10 I installed bridge-utils as a requirement for the openvpn server. According to the instructions on [http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04](http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04)
I set my /etc/network/interfaces like this:
```

auto lo
iface lo inet loopback
#iface eth0 inet static
#address 192.168.1.5
#netmask 255.255.255.0
#gateway 192.168.1.1
#dns-nameservers 192.168.1.1
#
auto br0
iface br0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports all
#
iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

```The problem is that when I boot the machine there is no network. However it comes back if I run:
% sudo /etc/init.d/networking restart
spitting out the following messages:
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-down.d/resolvconf exited with return code 1

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-up.d/000resolvconf exited with return code 1
ssh stop/waiting
ssh start/running, process 2857

```so I followed the advice on: [http://alanlupsha.blogspot.com/](http://alanlupsha.blogspot.com/) that is to kill NetworkManager and run:

% sudo dpkg-reconfigure resolvconf

and effectively the /etc/resolv.conf file was changed to a symlink to 

/etc/resolvconf/run/resolv.conf

However, when I boot the machine again, the /etc/resolv.conf is back to be a file and there is no network unless I run again:
% sudo /etc/init.d/networking restart
coming back with the same error messages as shown above.
Can someone figure this out? Thanks!

Daniel

---

### Post by danielsender on 2012-01-19
Anybody???

---

