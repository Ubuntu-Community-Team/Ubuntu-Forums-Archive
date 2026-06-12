---
title: "'Network not reachable' after every reboot"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by wjstarck on 2011-04-23
This began after upgrading to 11.4.

I have to manually do the following after every reboot:

```
sudo ifconfig eth0 up 192.168.1.137 netmask 255.255.255.0
sudo route add -net 0.0.0.0 gw 192.168.1.1 eth0
```

I have a static network interface, here's what's in /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet static
address: 192.168.1.137
netmask: 255.255.255.0
gateway: 192.168.1.1
dns-nameservers: 192.168.1.7 208.68.220.220 208.67.222.222

```

Any suggestions?

Thanks.

---

### Post by wjstarck on 2011-04-27
Going once....going twice...?

---

### Post by Sergei_K on 2011-04-27
in the interface file remove the # sign before "auto eth0"

---

### Post by wjstarck on 2011-04-27
I tried that but it gives me the following error when I try to restart networking:


```
 wjs@mail:~$ sudo /etc/init.d/networking restart
[sudo] password for wjs: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
Don't seem to have all the variables for eth0/inet0
Failed to bring up eth0 
```

So, growing tired of network-manager(it's always given me problems) I uninstalled it and went with wicd instead. Everything works perfectly now.

Thanks.

---

