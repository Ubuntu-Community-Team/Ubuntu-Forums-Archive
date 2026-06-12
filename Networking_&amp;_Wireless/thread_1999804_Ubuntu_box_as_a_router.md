---
title: "Ubuntu box as a router"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by skipsbro on 2012-06-08
I'm attempting to use an ubuntu box as a router so I can route traffic though squid to cache webpages and provide a small level of filtering. Currently, I have an old ubuntu box with two wired NICS. 

Details:

The NIC eth1 faces a router (and the internet) that must be in place, as our ISP uses MAC based authentication, and eth0 faces the network.

The network on the eth0 side is 192.168.2.0/24 and on the eth1 side is 192.168.1.0/24. Currently, the ubuntu box I am using can communicate to the internet, and the machines on the 192.168.2.0/24 network can talk to each other, but if I try to ping 192.168.1.1 (or any IP on the internet), the connection times out.

Does anyone have any information that might help? I can dump my iptables and route configurations if necessary.

---

### Post by SeijiSensei on 2012-06-08
Is IP packet forwarding enabled in the kernel?  To check, run "cat /proc/sys/net/ipv4/ip_forward" and see if it has a value of one.  If not, you need to edit /etc/sysctl.conf and follow the instructions in that file to enable IPv4 packet forwarding.  Reboot to make the changes take effect.

---

### Post by wlraider70 on 2012-06-09
you could spoof the the MAC on eth1 so it is directly connected to the internet.

---

