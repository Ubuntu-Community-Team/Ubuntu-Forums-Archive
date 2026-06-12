---
title: "Bonding + Bridge - after reboot bond has issues"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by nixgeek on 2010-08-31
Hey All,

My setup:
Kubuntu 10.04 {with most recent patches as of today}
A Quad Nic Bond
A Bridge

Ok I have had this issue for some time now... to no avail...

After a reboot I see this running dmesg...

164.666303] bond0: received packet with own address as source address
[  164.666314] bond0: received packet with own address as source address
[  164.666318] bond0: received packet with own address as source address
[  164.666324] bond0: received packet with own address as source address
[  164.666345] bond0: received packet with own address as source address
[  164.666351] bond0: received packet with own address as source address
[  164.666363] bond0: received packet with own address as source address
[  164.666367] bond0: received packet with own address as source address
[  164.666375] bond0: received packet with own address as source address

I have to /etc/init.d/networking restart and then it goes away.
# The loopback network interface

Here is my /etc/network/interface

auto lo
iface lo inet loopback

iface eth0 inet manual
iface eth1 inet manual
iface eth2 inet manual
iface eth3 inet manual

# The primary network interface
auto bond0
iface bond0 inet manual
slaves eth0 eth1 eth2 eth3
bond-miimon 200
bond-mode 6

auto br0
iface br0 inet static
address 192.168.0.67
netmask 255.255.255.0
gateway 192.168.0.101
bridge_ports bond0
bridge_fd 0
#bridge_hello 2
#bridge_maxage 12
bridge_stp off

I do not have any network manager installed.

# apt-show-versions | grep manag
kde-window-manager/lucid uptodate 4:4.4.2-0ubuntu14
kwalletmanager/lucid uptodate 4:4.4.2-0ubuntu1
libtaskmanager4/lucid uptodate 4:4.4.2-0ubuntu14
update-manager-core/lucid uptodate 1:0.134.10
update-manager-kde/lucid uptodate 1:0.134.10
virt-manager/lucid uptodate 0.8.2-2ubuntu8

Any Ideas?

---

### Post by ion-ral on 2011-01-04
> **nixgeek said:**
> Hey All,
 
My setup:
Kubuntu 10.04 {with most recent patches as of today}
A Quad Nic Bond
A Bridge
 
Ok I have had this issue for some time now... to no avail...
 
After a reboot I see this running dmesg...
 
164.666303] bond0: received packet with own address as source address
[ 164.666314] bond0: received packet with own address as source address
[ 164.666318] bond0: received packet with own address as source address
[ 164.666324] bond0: received packet with own address as source address
[ 164.666345] bond0: received packet with own address as source address
[ 164.666351] bond0: received packet with own address as source address
[ 164.666363] bond0: received packet with own address as source address
[ 164.666367] bond0: received packet with own address as source address
[ 164.666375] bond0: received packet with own address as source address
 
I have to /etc/init.d/networking restart and then it goes away.
# The loopback network interface
 
Here is my /etc/network/interface
 
auto lo
iface lo inet loopback
 
iface eth0 inet manual
iface eth1 inet manual
iface eth2 inet manual
iface eth3 inet manual
 
# The primary network interface
auto bond0
iface bond0 inet manual
slaves eth0 eth1 eth2 eth3
bond-miimon 200
bond-mode 6
 
auto br0
iface br0 inet static
address 192.168.0.67
netmask 255.255.255.0
gateway 192.168.0.101
bridge_ports bond0
bridge_fd 0
#bridge_hello 2
#bridge_maxage 12
bridge_stp off
 
I do not have any network manager installed.
 
# apt-show-versions | grep manag
kde-window-manager/lucid uptodate 4:4.4.2-0ubuntu14
kwalletmanager/lucid uptodate 4:4.4.2-0ubuntu1
libtaskmanager4/lucid uptodate 4:4.4.2-0ubuntu14
update-manager-core/lucid uptodate 1:0.134.10
update-manager-kde/lucid uptodate 1:0.134.10
virt-manager/lucid uptodate 0.8.2-2ubuntu8
 
Any Ideas?
 
bonding + bridging, try this bridge settings
 
**brigde_fd 0**
**bridge_stp off # switch on with more system like this**
**bridge_maxage 0**
**bridge_ageing 0**
**bridge_maxwait 0**
 
I do not know if it solves the problem on dmesg, but if you want to virtualize without problems in the presence of bonding bridging must be configured so absolutely

---

