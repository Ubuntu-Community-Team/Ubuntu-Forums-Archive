---
title: "Bridges and VLANs"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by Chrus on 2012-05-07
Got an Ubuntu box with 4 NICs. The plan is to have eth0 connected to a modem/interwebs, and have eth1, eth2 and eth3 in a bridge (br0). The bridge also needs to have a VLAN on it (br0.10).

In the past, I've done bridges and VLANs, but never at the same time. I've come close to getting it working, but its not quite right. With my current config, I'm getting br0 and br0.10 to come up with I reboot, however, /etc/init.d/networking restart will not bring up br0.10 (device br0.10 already exists; can't create bridge with the same name. Failed to bring up br0.10).

And having said that, even if this did work properly, it doesnt seem like the most elegant way of doing it.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
up /usr/local/firewall.sh

auto eth1.10
iface eth1.10 inet manual
    up ifconfig eth1.10 up
    
auto eth2.10
iface eth2.10 inet manual
    up ifconfig eth2.10 up

auto eth3.10
iface eth3.10 inet manual
    up ifconfig eth3.10 up

auto br0
iface br0 inet static
    address 172.30.40.1
    netmask 255.255.255.0
    pre-up ifconfig eth1 down
    pre-up ifconfig eth2 down
    pre-up ifconfig eth3 down
    pre-up brctl addbr br0
    pre-up brctl addif br0 eth1
    pre-up brctl addif br0 eth2
    pre-up brctl addif br0 eth3
    pre-up ifconfig eth1 0.0.0.0
    pre-up ifconfig eth2 0.0.0.0
    pre-up ifconfig eth3 0.0.0.0
    post-down ifconfig eth1 down
    post-down ifconfig eth2 down
    post-down ifconfig eth3 down
    post-down ifconfig br0 down
    post-down brctl delif br0 eth1
    post-down brctl delif br0 eth2
    post-down brctl delif br0 eth3
    post-down brctl delbr br0
    up /usr/local/firewall.sh

auto br0.10
iface br0.10 inet static
    address 172.30.44.1
    netmask 255.255.255.0
    pre-up ifconfig eth1.10 down
    pre-up ifconfig eth2.10 down
    pre-up ifconfig eth3.10 down
    pre-up brctl addbr br0.10
    pre-up brctl addif br0.10 eth1.10
    pre-up brctl addif br0.10 eth2.10
    pre-up brctl addif br0.10 eth3.10
    pre-up ifconfig eth1.10 0.0.0.0
    pre-up ifconfig eth2.10 0.0.0.0
    pre-up ifconfig eth3.10 0.0.0.0
    post-down ifconfig eth1.10 down
    post-down ifconfig eth2.10 down
    post-down ifconfig eth3.10 down
    post-down ifconfig br0.10 down
    post-down brctl delif br0.10 eth1.10
    post-down brctl delif br0.10 eth2.10
    post-down brctl delif br0.10 eth3.10
    post-down brctl delbr br0.10
    up /usr/local/firewall.sh


```

---

### Post by Chrus on 2012-05-08
Bump!

---

### Post by Chrus on 2012-05-09
Anyone have any words of wisdom on this subject?

---

### Post by marila809 on 2012-05-09
[COLOR=#000000][FONT=arial]nter-VLAN bridging is the concept of simultaneously bridging multiple VLANs together. Inter-VLAN bridging is occasionally needed in order to bridge non-routable protocols or unsupported routed protocols between multiple VLANs.
[web design Sydney](http://www.rcmwebsitedesign.com.au/)
[website design sydney](http://www.rcmwebsitedesign.com.au/)

[/FONT][/COLOR]

---

### Post by Chrus on 2012-05-11
Nevermind. I worked it out for myself.

---

### Post by mid_crisis on 2012-07-29
Hey! Can you share your solution please?
I'm pulling my hair out trying to configure three bridges on a VLAN to end up llike this

Hey! Can you share your solution please?
I'm pulling my hair out trying to configure three bridges on a VLAN to end up llike this

```

eth0----+
        |              +----vlan1----br1
eth1----+              |
        |-----bond0----+----vlan2----br2
eth2----+              |
        |              +----vlan3----br3
eth3----+
```

tagged traffic on hitting bond0 and being delivered to the respective bridges.

Thanks!

tagged traffic on hitting bond0 and being delivered to the respective bridges.

Thanks!

---

