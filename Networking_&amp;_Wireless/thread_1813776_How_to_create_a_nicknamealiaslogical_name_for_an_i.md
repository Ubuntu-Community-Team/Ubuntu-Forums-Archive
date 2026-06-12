---
title: "How to create a nickname/alias/logical name for an interface"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by tdiy on 2011-07-28
Hi,

Basically I am looking for a simple way to create a universal nickname/alias for a interface.
We ship servers that have upto 6 NICs on them. The user can have those NIC configured as either ethN, bondN or vlanN interfaces. As we need to provide NIC status information we would like to be able to run commands such as
```
ifconfig INTERFACE1
```that would map to whatever the user had already configured.

So INTERFACE1 could represent eth0 or bond0 or vlan100 or whatever.

Is that possible?

Cheers
Thomas

---

### Post by tdiy on 2011-08-10
Well after trawling the web, experimenting with ALL sorts of ideas and even screwing up the boot sequence due to a bug in /etc/network/interface file ([https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)) I finally figured out what I needed to know.

By setting up a bridged interface. I can now have a fixed named interface that lives on top of either a VLAN a bonded interface or just the plain ordinary physical eth interface.

You will need to install bridge-utils
```
sudo apt-get install bridge-utils
```and your /etc/network/interface files should look something like this 

```

auto bond0
iface bond0 inet manual
bond-slaves eth0 eth1  
bond_mode 1  
bond_miimon 100

auto WHATEVER-NAME-YOU-LIKE 
iface WHATEVER-NAME-YOU-LIKE inet static     
address 10.1.3.1     
netmask 255.255.255.0     
vlan-raw-device bond0     
bridge_ports vlan50 

```which gives you the following interface chain
WHATEVER-NAME-YOU-LIKE  <-> vlan50 <-> bond0 <-> (eth0 & eth1)  

Credit goes to [http://inodes.org/2007/04/30/ubuntu-vlans-and-bridges/](http://inodes.org/2007/04/30/ubuntu-vlans-and-bridges/) for opening my eyes to bridging

Ttttthat's it folks :)

Apparently trying to get  DHCP working with a bridged bonded interface requires something like this

```

auto bond0
iface bond0 inet manual
bond-slaves none
bond_mode 1
bond_miimon 100  

auto eth0
allow-bond0 eth0
iface eth0 inet manual
bond-master bond0

auto WHATEVER-NAME-YOU-LIKE
iface WHATEVER-NAME-YOU-LIKE inet dhcp     
bridge_ports bond0
bridge_maxwait 0
bridge_fd 0
   

```

---

