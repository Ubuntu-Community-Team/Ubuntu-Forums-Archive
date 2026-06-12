---
title: "ICS cant get it to work correctly"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by EMKOEMO on 2009-11-22
im trying to share internet from my ubuntu pc to a laptop with crossover cable so far i only go it so i can connect with ftp and ssh with the laptop but i cant connect to the internet on both.    

I used  

#!/bin/sh
#
# internet connection sharing wlan0 is the gate way
# eth0 is the lan port this might use a straight ethernet cable to a router wan port or a switch or a single PC
# 192.168.2.2 is the port that is being used by the lan for access I changed it to 192.168.2.254 and set fixed addresses for the wan and router
#
# change wlan0 to ppp0 and you can use this for mobile broadband connection sharing
#
ifconfig eth0 up"
ifconfig eth0 192.168.2.1
echo “1” > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.2
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p udp -m multiport --dports 88,3074 -j ACCEPT



my interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-essid linksysX3
wireless-channel 10
wireless-key XXXXXXXX

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

if i remove everything and set wlan0 to dhcp and put in the wireless info the internet works i can ping google.com

my laptop i put ip 192.168.0.13 subnet 255.255.255.0  gateway 192.168.0.1 how can i fix this?

---

### Post by EMKOEMO on 2009-11-22
i tried this

sudo ifconfig wlan0 192.168.1.100
sudo iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Witch made my laptop finaly connect to the internet but the ubuntu pc that im geting the internet from is not able to access the internet or ping google.com.

so confusing :( im running XBMClive which is based of karmic so i have no user interface which probably would make it easier but i don't need it.

---

### Post by EMKOEMO on 2009-11-22
ok i figured something out when i set wlan0 to dhcp i get connection on both pc and laptop but i need static ip address can someone please tell me what im doing wrong with the static ip address in my interfaces/

---

### Post by EMKOEMO on 2009-11-22
ok got both working correctly untill i rebooted. i have to type

sudo iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

if i dont type this i get internet only on pc and on laptop i can only connect to the pc with ssh and ftp once i type those commands i get internet on both pc and laptop is there any way to make this stay like this always?

---

