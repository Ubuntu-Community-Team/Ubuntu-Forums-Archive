---
title: "Recent upgrade to 11.04, after reboot Ethernet is blind to the rest of the network"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by keesercc on 2011-05-01
Everything was working well in 10.10.  I upgraded to 11.04 and after a reboot, the eth0 interface is essentially blind to my network.  I have an ubuntu server that runs dnsmasq to function as the DHCP server on my network.

On my failing machine, I cannot connect to any website, I cannot ping any device in my network and I cannot see any other device in my network using nmap.

NetworkManager on the failing machine has been configured to use DHCP and when that failed, I tried a static IP address.  That has also failed.  I have edited the /etc/network/interfaces to use both DHCP and static ip addresses and rebooted in between each change just to be sure.

Pings to my router and server from the failing box return "destination host is unreachable" and the result of nmap -sP 192.169.1.1/24 show only my machine with it's static ip address and nothing else.  The failing machine can successfully ping itself when I ping it's static ip address.  The dhcp server box is unable to ping the failing machine but is able to ping all other devices on the network.  Running the same nmap command on the server shows shows 10+ devices on the network, but not my failing machine.

I'm at the end of my Linux knowledge (and my rope) and need assistance. 

My server resides at 192.168.1.2, router at 192.168.1.1 and the dhcp server is set up to assign addresses in the 192.168.1.50 to 192.168.1.150 range.  When assigning my failing machine to a static ip, I use 192.168.1.151, subnet 255.255.255.0, gateway 192.168.1.1.

I am grateful for any help.  Thank you.

---

### Post by keesercc on 2011-05-01
*mumble mumble* flaky ethernet cable *mumble mumble*

problem solved.

---

