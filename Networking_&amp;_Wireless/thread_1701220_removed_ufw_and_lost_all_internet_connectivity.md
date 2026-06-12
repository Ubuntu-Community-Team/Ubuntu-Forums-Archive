---
title: "removed ufw and lost all internet connectivity"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by jimbean on 2011-03-06
i was having trouble with some software detecting ports so i removed ufw and now have no internet

ive tried and none of these work

gksudo /etc/init.d/networking restart


!/bin/sh 
sudo /etc/init.d/networking restart; sudo dhclient 


sudo ifconfig eth0 down; sudo ifconfig eth0 up; sudo dhclient 



ifconfig



* Attempts to renew the DHCP lease, if the connection obtains its IP address through DHCP, using a broadcast message.
* Flushes the Address Resolution Protocol (ARP) cache using the command

arp -d * 

* Flushes the NetBIOS cache using the command

nbtstat -R

* Flushes the DNS cache using the command

ipconfig /flushdns

* Reregisters the NetBIOS name and IP address with WINS using the command

nbtstat -RR 

* Reregisters the computer name and IP address with DNS using the command

ipconfig /registerdns

---

### Post by jimbean on 2011-03-06
ok back on internet after reinstalling ufw
and manually setting all of the ipv4 settings in network connections
the problem is
are these correct
address 192.168.0.10
dns server 212.143.212.143
gateway 192.168.0.1
netmask 255.255.255.0
 then i reset
sudo dhclient
is this correct or am i in need of fine tuning

i got these settings off of another ubuntu forum post

---

