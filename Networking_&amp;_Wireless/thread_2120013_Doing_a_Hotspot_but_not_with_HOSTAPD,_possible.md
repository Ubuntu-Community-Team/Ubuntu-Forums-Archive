---
title: "Doing a Hotspot but not with HOSTAPD, possible?"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by Surabaya on 2013-02-25
Hi, 

I tried HOSTAPD. It works but randomly disconnect my internet connexion and/or my USB modem. So i try to find a simple solution to: share my 3G Internet connection coming from a USB modem, through the wifi. And i would like to give a fix ip to the wireless card sharing the 3G. Then my Android phone could use my 3G connexion. 
I cannot do this by an AD HOC network: Android phones cannot see ad hoc networks.

I found this script:

```

#!/bin/bash
###############################
### Configure Managed WiFi
###############################
#sudo service network-manager stop
sudo ifconfig -v wlan0 down
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 channel 11
sudo iwconfig wlan0 essid Poyette
sudo iwconfig wlan0 rate 54M
#sudo iwconfig wlan0 key poyoswan
sudo iwconfig wlan0 ap off
sudo ifconfig -v wlan0 10.0.0.33 netmask 255.255.255.0
sudo ifconfig -v wlan0 up
 
#seems to set wifi power to minimum
sudo iwconfig wlan0 txpower 0
 
 
###############################
### Set up NAT Routing
###############################
### Simple "insecure" nat - DO NOT USE (TESTING ONLY)
#sudo sysctl net.ipv4.ip_forward=1
#sudo iptables -P FORWARD ACCEPT
#sudo iptables --table nat -A POSTROUTING -o ppp0 -j MASQUERADE
 
#Temporarily block all traffic
sudo sysctl net.ipv4.ip_forward=0
sudo iptables -P OUTPUT DROP
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
 
# Delete/Flush old iptables rules
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -X
 
# Set default policies
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
 
# Prevent external packets from using loopback addresses [OPTIONAL]
sudo iptables -A INPUT   -i ppp0 -s 127.0.0.1 -j DROP
sudo iptables -A INPUT   -i ppp0 -d 127.0.0.1 -j DROP
sudo iptables -A FORWARD -i ppp0 -s 127.0.0.1 -j DROP
sudo iptables -A FORWARD -i ppp0 -d 127.0.0.1 -j DROP
 
# Anything coming from/going to Internet should not
# use private addresses [OPTIONAL]
sudo iptables -A INPUT   -i ppp0 -s 172.16.0.0/12  -j DROP
sudo iptables -A INPUT   -i ppp0 -s 10.0.0.0/8     -j DROP
sudo iptables -A INPUT   -i ppp0 -s 192.168.0.0/24 -j DROP
sudo iptables -A FORWARD -i ppp0 -s 172.16.0.0/12  -j DROP
sudo iptables -A FORWARD -i ppp0 -s 10.0.0.0/8     -j DROP
sudo iptables -A FORWARD -i ppp0 -s 192.168.0.0/24 -j DROP
 
#Extra security stuff
sudo iptables -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags ALL ALL -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP 
 
# Block outgoing NetBios [OPTIONAL]
sudo iptables -A FORWARD -p tcp --sport 137:139 -o ppp0 -j LOG --log-prefix "FORWARD DROP: "
sudo iptables -A FORWARD -p tcp --sport 137:139 -o ppp0 -j DROP
sudo iptables -A FORWARD -p udp --sport 137:139 -o ppp0 -j LOG --log-prefix "FORWARD DROP: "
sudo iptables -A FORWARD -p udp --sport 137:139 -o ppp0 -j DROP
sudo iptables -A OUTPUT  -p tcp --sport 137:139 -o ppp0 -j LOG --log-prefix "OUTPUT DROP: "
sudo iptables -A OUTPUT  -p tcp --sport 137:139 -o ppp0 -j DROP
sudo iptables -A OUTPUT  -p udp --sport 137:139 -o ppp0 -j LOG --log-prefix "OUTPUT DROP: "
sudo iptables -A OUTPUT  -p udp --sport 137:139 -o ppp0 -j DROP
 
# Allow local loopback [NEEDED]
sudo iptables -A INPUT -i lo -j ACCEPT
 
# Allow pings [OPTIONAL]
sudo iptables -A INPUT   -p icmp --icmp-type echo-request -j ACCEPT
sudo iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT
 
# START STATE STUFF
# Accept existing connections [NEEDED]
sudo iptables -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
 
# Allow any new conections from internal network
# [ONLY NEEDED IF PORTS ARE NOT EXPLITLY FORWARDED BELOW]
sudo iptables -A INPUT -m state --state NEW -i wlan0 -j ACCEPT
# I *think* this would allow *all* outbound instead of just explicit ports permitted below
#sudo iptables -A FORWARD -m state --state NEW -i wlan0 -o ppp0 -j ACCEPT
# END STATE STUFF
 
# Internal inbound services [OPTIONAL - DNS NEEDED]
#sudo iptables -A INPUT -p udp -i wlan0 --dport 53      -m state --state NEW -j ACCEPT #DNS cache
#sudo iptables -A INPUT -p tcp -i wlan0 --dport 53      -m state --state NEW -j ACCEPT #DNS cache
#sudo iptables -A INPUT -p udp -i wlan0 --dport 137:139 -m state --state NEW -j ACCEPT #SAMBA
#sudo iptables -A INPUT -p tcp -i wlan0 --dport 445     -m state --state NEW -j ACCEPT #SAMBA
 
# Allow forwarding of essential services [NEEDED]
sudo iptables -A FORWARD -p tcp --dport 53 -j ACCEPT #DNS
sudo iptables -A FORWARD -p udp --dport 53 -j ACCEPT #DNS
sudo iptables -A FORWARD -p tcp --dport 80 -j ACCEPT #WEB
sudo iptables -A FORWARD -p tcp --dport 81 -j ACCEPT #WEB
sudo iptables -A FORWARD -p tcp --dport 443 -j ACCEPT #HTTPS
sudo iptables -A FORWARD -p tcp --dport 143 -j ACCEPT #IMAP
sudo iptables -A FORWARD -p tcp --dport 993 -j ACCEPT #IMAP SSL
sudo iptables -A FORWARD -p tcp --dport 995 -j ACCEPT #YAHOOMAIL?
sudo iptables -A FORWARD -p tcp --dport 25 -j ACCEPT #SMTP
sudo iptables -A FORWARD -p tcp --dport 465 -j ACCEPT #SMTP SSL
sudo iptables -A FORWARD -p tcp --dport 5223 -j ACCEPT #IPHONE PUSH
sudo iptables -A FORWARD -p tcp --dport 2195 -j ACCEPT #IPHONE PUSH
sudo iptables -A FORWARD -p tcp --dport 1919 -j ACCEPT #IPHONE PINGCHAT!
 
# Masquerade [NEEDED]
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
 
# Enable routing.
sudo sysctl net.ipv4.ip_forward=1
```When i start he script, it gives me:

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Network is down.
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Network is down.
net.ipv4.ip_forward = 0
net.ipv4.ip_forward = 1


Strange, my network is up...
Also no Wifi Network was created and detected by any other computer.

Any one could help me to correct this problem and make this script working without dhcp server but with a fix IP? 

One thousand thanks in advance.

Surabaya

---

