---
title: "which method of forwarding?-10.04 server"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-10-14
Ok so server will pass mostly wired LAN clients through eth1 to eth0 and adsl modem router. internet--adsl modem/router--eth0--server--eth1--switch--LAN. I realize now there are several ways to do this. It occured to me that ultimately everything has to work together, so plan to use: ufw for firewall, samba for windows file server, dhcp3 to serve LAN. I'd like to choose between setting up forwarding in: iptables, ufw, dnsmasq, bind9,sysctl.conf, and net-manager(?). I've started down a path several times only to discover that a later installed package or service creates a conflict, so this time I want it clean and simple.
auto eth0
iface eth0 inet dhcp
 
auto eth1
iface eth1 inet static
address 10.10.0.1
netmask 255.255.255.0
gateway 192.168.1.1
 
I have started dhcp3 with a range of 10.10.0.10 10.10.0.150
testclient is getting ip 10.10.0.10 but won't ping past 127.0.0.1
i did make an attempt at forwarding, but i was tired last night and may have made some entries with both the iptables approach and the sysctl.conf , so I'm at a juncture where i could format (again) and start over, or clean it up. Just want some guidance here so I don't waste more time.

---

