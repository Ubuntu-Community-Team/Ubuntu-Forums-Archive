---
title: "PXE from other subnet"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by gregsheu on 2009-01-26
Any PXE guru, please help.
We have PXE server in subnet A 192.168.2.0/24, and all workstations in this subnet can net boot and install the OS from TFTP sever without any issue. We recently add another router to assign the IP to antoher subnet B 192.168.3.0/24. The workstations in subnet B are assigned by DHCP from the router that has two nic connected respectively to subnet A (eth0) and subnet B (eth1). The eth0 is 192.168.2.x and eth1 is 192.168.3.1 to assign DHCP IP to subnet B. All workstations in both subnets can ping each other, ssh or VNC mutually without issue. The router B serves only as router, no firewall, because it is the internal router to connect two different subnets. Is that anyway that the subnet B can netboot to connect to the TFTP server in subnet A? I've been searching, and there are some suggestion saying using dhcp-relay or using vlan like ip help-address(Cisco). But we don't have Cisco equipment, and I've tried dhcp-relay, but it doesn't work. 
Any help will be greatly appreciated.

---

