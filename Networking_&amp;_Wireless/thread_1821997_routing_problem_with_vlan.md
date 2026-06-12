---
title: "routing problem with vlan?"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by mimizone on 2011-08-09
Hi All,
the following problem has been tested with Ubuntu 9.04 and 11.04.

I have the following test setup

**Server1 (let's call it pxeserver)**
eth0: static on 10.33.176.3/24
2 vlans
eth1.50: 10.1.0.1/24
eth1.51: 172.30.4.2/22

routing table:
10.33.176.0/24 on eth0
10.1.0.0/24 on eth1.50
172.30.4.0/22 on eth1.51
default gateway is 172.30.4.1 on eth1.51

**Server2 (let's call it client)**
eth0: static on 172.30.5.3/22

routing table:
172.30.4.0/24 on eth0
default 172.30.4.1 on eth0

**network:**

Server1(pxeserver) <--(trunk 51 and 50)              --> Switch1 <--(trunk 51,50) --> Router
Server2(client)        <--(trunk with native vlan 51) --> Switch1

for those that want to know:
server1: ubuntu 9.04 or 11.04
server2: centos 5.6
switch: Cisco NExus 5548
Router: Cisco VXR 7206

Router has 2 interfaces:
Ethernet 4/2.50 with ip address 10.1.0.1/24
Ethernet 4/2.51 with ip address 172.30.4.1/22


The idea behind this setup is to have a pxeserver with the IP 10.1.0.10 on VLAN50
and other VLAN such as 51 (52,53,etc...) able to DHCP/PXE boot and be forwarded to the pxeserver 10.1.0.10 via TFTP.

**problem:**
the client cannot ping 10.1.0.10 (the pxe server).
the pings are received on the pxeserver side, but never sent back.
There is no trace in tcpdump of the server1 trying to send back anything to the client on any interface. (eth0, eth1.50, eth1.51)

the pings are received on the eth1.50

a weird thing that I can't explain either is that if a route is set on the client as follow
route add -net 10.1.0.0 netmask 255.255.255.0  eth0

the ping are received on the pxeserver side on the other VLAN (51) and in that case sent correctly back via that same VLAN.

both pxeserver and client see properly the IP addresses of the router and can connect to each other on the VLAN51 (172.30.4/22).

any thoughts?
I pulled my hair many times on this and I am out of ideas.

---

### Post by mimizone on 2011-08-10
didn't solve the problem with the previous setup. I tried enabling the ip_forwarding, but it doesn't help (wasn't really believing it would anyway...)

I wonder if the overall problem is because the different VLAN interfaces have the same MAC address ??

I ended up just changing the setup, having only one interface on 10.1.0.0/24 on the pxeserver and use the "ip helper-address 10.1.0.10" in the router to forward broadcast from other interfaces.

---

### Post by mimizone on 2011-08-15
it appears the initial issue may have been because the rp_filter flags are enabled by default in the kernel network configuration and must be disabled in such a multi homing configuration.

---

