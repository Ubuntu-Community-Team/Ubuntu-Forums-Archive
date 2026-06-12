---
title: "Multiple Network bridges on ubuntu server."
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by sona1111 on 2012-02-11
Hello people. I am having a few problems setting up network bridges on a server. The hardware is a ibm xseries 366, 8 cpus, integrated video, 2 gb memory. The network interfaces are all wired twisted pair 10/100/1000 ports. Two are planar called by ubuntu eth0 and eth1. Their are eight more on four pci-x cards. Ubuntu calls these eth2, 3, 4, 5, 8, 9, 10, and eth11 (why did it skip six and seven? no idea)

First i figured out a bridge between three of the ports, eth 8 has the internet and dhcp server, and eth10 and eth4 are currently outputs. I am having a problem creating a second bridge between eth0 and eth1 eth0 has the dhcp server and internet and i need it to have a static ip. (preferred 192.168.2.70 because it is port forwarded correctly, but can change if needed.) The other outgoing connection eth1 should be ablt to connect other computers to the dhcp server on eth0 and connect then to the internet. In my various attempts it has never sent any packets on eth1. Here is my current interfaces file...:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# List of Network interfaces (hot plug)
#Earthlink Internet
auto eth0
iface eth0 inet dhcp
#address 192.168.2.70
#gateway 192.168.2.1
#netmask 255.255.255.0
#network 192.168.2.0

#Earthlink Output (ftp trans)
auto eth1
iface eth1 inet manual
#address 192.168.2.220
#netmask 255.255.255.0
up ip link set eth1 up

#wireless input
auto eth8
iface eth8 inet dhcp
#address 192.168.2.80
#gateway 192.168.2.4
#netmask 255.255.255.0
#network 192.168.2.0

#gigabit output
auto eth4
iface eth4 inet manual
up ip link set eth4 up

#main output
auto eth10
iface eth10 inet manual
up ip link set eth10 up

#wireless main bridge
auto br0
iface br0 inet static
bridge_ports eth8 eth4 eth10
bridge_fd 0
bridge_hello 2
bridge_maxage 12
bridge_stp off
address 192.168.2.82
gateway 192.168.2.4
netmask 255.255.255.0

#earthlink secondary bridge
auto br1
iface br1 inet static
bridge_ports eth0 eth1
bridge_fd 0
bridge_hello 2
bridge_maxage 12
bridge_stp off
address 192.168.2.71
gateway 192.168.2.1
netmask 255.255.255.0

```

Thanks for reading.

---

### Post by sona1111 on 2012-02-12
bump

---

### Post by bakegoodz on 2012-02-12
I might know why you have missing interface numbers.
Did you have other cards plugged into this computer? Check /etc/udev/rules.d/70-persistent-net.rules see which card is assigned to each interface name. This command will probably help you keep straight which is which in the file: lshw -short -C network -numeric

Or you could use "lshw -C network" which will give mac addresses, but may be too hard to read with that many NICS.

I'll try to help you with your bridges too, but I need more information.
Giving the output of the following command will help
 brctl show

---

### Post by sona1111 on 2012-02-13
sorry for the long resaponse.

The output shows both bridges.

bridge name: br0, br1
bridge id 8000.0002a54e35b9, 8000.00110a5c2228 
stp enable no, yes  (?)
interfaces eth10 eth4 eth8, eth0 eth1

thank you again.

---

