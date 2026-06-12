---
title: "wireless accesspoint script help"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by 74kumi on 2011-12-13
Ok so my plan for this "project" was to set up my laptop to sorta act as a wireless repeater with my laptop in the middle. By using the laptops built in WiFi as the internet I'm sharing and a second WiFi adapter as the access point. The adapter I'm using is a ALFA b/g/n long range wireless my computer recognizes it as Ralink 802.11n WLAN. I have been using as many tutorials as i can find to help me out and this is what ive come up with so far
```
#!/bin/sh

echo "Tap is starting up"

echo "Changeing Interfaces"

mv /etc/network/interfaces backup
mv /etc/network/wireup interfaces

echo "Configuring firewall"

sudo iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -s 10.1.1.0/24 -o wlan0 -j ACCEPT
sudo iptables -A FORWARD -d 10.1.1.0/24 -m conntrack --ctstate ESTABLISHED,RELATED -i wlan0 -j ACCEPT

echo "Forwording Packets"
echo net.ipv4.ip_forward = 1 >> /etc/sysctl.conf

echo "subnet 10.1.1.0 netmask 255.255.255.0 {" >> /etc/dhcp/dhcpd.conf
echo "        option domain-name-servers 10.1.1.1;" >> /etc/dhcp/dhcpd.conf
echo "        max-lease-time 7200;" >> /etc/dhcp/dhcpd.conf
echo "        default-lease-time 600;" >> /etc/dhcp/dhcpd.conf
echo "        range 10.1.1.50 10.1.1.60;" >> /etc/dhcp/dhcpd.conf
echo "        option subnet-mask 255.255.255.0;" >> /etc/dhcp/dhcpd.conf
echo "        option broadcast-address 10.1.1.255;" >> /etc/dhcp/dhcpd.conf
echo "        option routers 10.1.1.1;" >> /etc/dhcp/dhcpd.conf
echo "        }" >> /etc/dhcp/dhcpd.conf

service networking restart
#service dhcpd restart #need a way to restart this...

```

at this point i need some help i lost the first tutorial i was using and was hoping someone knew how to do something like this. and if there is a way to make a script appear in network manager to make this a little more "desktop oriented" that would be awesome.

---

### Post by 74kumi on 2011-12-15
To add to this i finished the reset script for the start up script.
```
#!/bin/sh

echo "Tap is shuting down"

echo "Removing dhcpd configuration"

rm /etc/dhcp/dhcpd.conf

echo "Removing Forwarding Packet Forward"

rm /etc/sysctl.conf

echo "clearing IPTABLES"

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

echo "reverting back to standard interfaces"
mv /etc/network/interfaces /etc/network/wireup
mv /etc/network/backup /etc/network/interfaces

echo " restarting services"

service networking restart
service udhcpd start

echo "Tap is Down"

```
I do not recommend using this script on say a router or a machine that you have your own custom iptables lists
I also think i finished the tapup script
```
#!/bin/sh

echo "Tap is starting up"

echo "Changeing Interfaces"

mv /etc/network/interfaces /etc/network/backup
mv /etc/network/wireup /etc/network/interfaces

echo "Configuring firewall"

sudo iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -s 10.1.1.0/24 -o wlan0 -j ACCEPT
sudo iptables -A FORWARD -d 10.1.1.0/24 -m conntrack --ctstate ESTABLISHED,RELATED -i wlan0 -j ACCEPT

echo "Forwording Packets"
echo net.ipv4.ip_forward = 1 >> /etc/sysctl.conf

echo "subnet 10.1.1.0 netmask 255.255.255.0 {" >> /etc/dhcp/dhcpd.conf
echo "        option domain-name-servers 10.1.1.1;" >> /etc/dhcp/dhcpd.conf
echo "        max-lease-time 7200;" >> /etc/dhcp/dhcpd.conf
echo "        default-lease-time 600;" >> /etc/dhcp/dhcpd.conf
echo "        range 10.1.1.50 10.1.1.60;" >> /etc/dhcp/dhcpd.conf
echo "        option subnet-mask 255.255.255.0;" >> /etc/dhcp/dhcpd.conf
echo "        option broadcast-address 10.1.1.255;" >> /etc/dhcp/dhcpd.conf
echo "        option routers 10.1.1.1;" >> /etc/dhcp/dhcpd.conf
echo "        }" >> /etc/dhcp/dhcpd.conf

echo "restarting services"
service networking restart
service udhcpd start

echo "Tap is Up"

```

Right now i just need someone to run through this and help me set this up so wlan1 will appear as a access point and wlan0 will stay connected to the internet... i also need to know how to configure wlan1 in that way and/or see if i can

---

