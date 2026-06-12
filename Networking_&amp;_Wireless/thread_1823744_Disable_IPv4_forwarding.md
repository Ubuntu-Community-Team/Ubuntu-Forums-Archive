---
title: "Disable IPv4 forwarding"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by jbushman on 2011-08-12
I just installed Ubuntu 11.04 Server. My machine has two ethernet interfaces. I want to disable IPv4 forwarding between the interfaces. From what I've read, IP forwarding is disabled by default, but that was not my experience: it was **enabled** by the default installation.

I added this line to my /etc/sysctl.conf

net.ipv4.ip_forward=0

and it does disable IP forwarding if I run sysctl -p /etc/sysctl.conf, but IP forwarding does not stay disabled across restarts.

Is there some other file I need to edit to disable IP forwarding?  Here is my /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# office config
# iface eth0 inet static
#    address 10.88.5.50
#    netmask 255.255.255.0
#    network 10.88.5.0
#    broadcast 10.88.5.255
#    gateway 10.88.5.1
    # dns-* options are implemented by the resolvconf package, if installed
#    dns-nameservers 10.88.3.199 10.88.3.5
#    dns-search atl.ciena.com
iface eth0 inet static
    address 192.168.5.3
    netmask 255.255.255.0
    network 192.168.5.0
    broadcast 192.168.5.255
#    gateway 192.168.5.1
    # dns-* options are implemented by the resolvconf package, if installed
#    dns-nameservers 10.88.3.199 10.88.3.5
#    dns-search atl.ciena.com
# The secondary network interface
auto eth1
iface eth1 inet static
    address 192.168.205.3
    netmask 255.255.255.0
    network 192.168.205.0
    broadcast 192.168.202.255
    gateway 192.168.205.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 10.88.3.199 10.88.3.5
    dns-search atl.ciena.com

---

### Post by Toz on 2011-08-12
Welcome to the forums. 

Have a look at the files:
- /etc/default/ufw
...and
- /etc/ufw/sysctl.conf

I don't have an ubuntu server install to confirm, but it looks like the value is set and managed in the /etc/ufw/sysctl.conf file.

---

### Post by jbushman on 2011-08-15
Thanks for the reply and the welcome. I don't think I'm running ufw. The command
$ sudo ufw status
returns
  Status: inactive

Changing /etc/ufw/sysctl.conf also didn't seem to change anything.

---

### Post by Toz on 2011-08-15
Try running the following commands to see if it is specified anywhere else:
```
sudo bash -i
find /etc -print | xargs fgrep ip_forward
find /etc -print | xargs fgrep forwarding
```

EDIT: added one more command to run

---

### Post by jbushman on 2011-08-15
I tried
```
find /etc -print | xargs fgrep -i forward
```but didn't find anything.

Trying a different tack, it seems that the I have a virbr0 device, implying that virtualization library is in use, and that is probably is turning on IP forwarding.

```
virbr0    Link encap:Ethernet  HWaddr ba:a7:f6:3c:ff:01  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@gaxp-swlab-01:/etc# virsh net-list --all
Name                   State        Autostart
-----------------------------------------
default                active       yes       
```

---

