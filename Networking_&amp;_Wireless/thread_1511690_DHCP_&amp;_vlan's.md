---
title: "DHCP &amp; vlan's"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Valentin_X on 2010-06-17
Hello everyone,

i have set up a server with nfs and so on. now we have to have some changes here and i have do provide a dhcp server for a specific vlan. 
Can anyone help me with that?

my system currently running with 4 nic's bond to bond0 and bond1 and 3 vlan's

auto bond0
iface bond0 inet manual
	up ifconfig bond0 0.0.0.0 up
	bond_mode 802.3ad 
	bond_miimon 100
	bond_downdelay 200
	bond_updelay 200
	slaves eth0 eth1

auto bond1
iface bond1 inet manual
	up ifconfig bond1 0.0.0.0 up
	bond_mode 802.3ad 
	bond_miimon 100
	bond_downdelay 200
	bond_updelay 200
	slaves eth2 eth3

auto bond0.1000
iface bond0.1000 inet static
        address 10.168.XXX.XXX
        netmask 255.255.255.0
        broadcast 10.168.XXX.255
        network 10.168.XXX.0
        gateway 10.168.XXX.254
        vlan-raw-device bond0

auto bond1.4000
iface bond1.4000 inet static
        address 192.168.XXX.XXX
        netmask 255.255.255.0
        broadcast 192.168.XXX.255
        network 192.168.XXX.0
        gateway 192.168.XXX.254
        vlan-raw-device bond1

auto bond1.4001
iface bond1.4001 inet static
        address 192.168.XXX.XXX
        netmask 255.255.255.0
        broadcast 192.168.XXX.255
        network 192.168.XXX.0
        gateway 192.168.XXX.254
        vlan-raw-device bond1

how to setup the dhcp to only provide his service to vlan bond1.4000 ?

---

### Post by jonobr on 2010-06-18
I havent done this myself, but I find the question v interesting.

I did some snooping around and found [ This ]("http://onvox.net/linux/how-to-enable-8021q-vlan-tagging-in-ubuntu") interesting article, 
its old, (2 years) and discusses loading the dot1q module for supporting vlan tagging.

I guess you have already done all that , so all im really doing is giving you a bump and hope someone sees this who has done it before

---

### Post by Valentin_X on 2010-06-21
--bump--

---

