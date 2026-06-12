---
title: "How to bridge a wireless LAN"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by chele on 2011-07-30
I am trying to connect networks connected via locked down wireless routers. Here is the setup: 
 
Internet <-> eth0 - server - eth1 providing DHCP <-> hub <-> wired clients & to WiFi router with NAT & DHCP <-> WiFi clients. 

I want the wired clients and the WiFi clients to be able to talk to each other directly, but the locked down WiFi router (meraki) is in the way. the wired clients get their IP address from the server, the wireless clients get theirs from the meraki wifi router. I can't reconfigure the wifi router to bridged mode without paying meraki a sizeable annual license fee. What options are out there to get through the wifi router? 
 
I came across OpenVPN and ethernet bridging, but broke networking on the server when trying to configure the br0 interface. Is this the right way to go, or is there something simpler? 
 
I followed these instructions: 
 
[https://help.ubuntu.com/10.10/serverguide/C/openvpn.html](https://help.ubuntu.com/10.10/serverguide/C/openvpn.html) 
[https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html#bridging)

---

### Post by chele on 2011-07-30
Here is the original network setup> auto lo
iface lo inet loopback

auto eth0
     iface eth0 inet dhcp

auto eth1
     iface eth1 inet static
     address 172.16.0.1
     netmask 255.255.0.0
     gateway 172.16.0.1And here is what I tried for the bridge, but this broke all network connections> auto lo
iface lo inet loopback

auto eth0
     iface eth0 inet dhcp

auto br0
iface br0 inet static
        address 172.16.8.1
        network 172.16.0.0
        netmask 255.255.0.0
        broadcast 172.16.255.255
        gateway 172.16.8.1
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by chele on 2011-07-31
This link: [http://www.serverubuntu.it/openvpn-bridge-configuration](http://www.serverubuntu.it/openvpn-bridge-configuration) helps a bit. Looks like I need to use different network ranges in ifconfig and in the openvpn config file.

Bad news may be the note at the bottom about configuring the router to forward UDP port 1194. I can't do that, as meraki has locked down the router (which is hte whole reason for this exercise). I guess I'll find out one way or another ...

---

