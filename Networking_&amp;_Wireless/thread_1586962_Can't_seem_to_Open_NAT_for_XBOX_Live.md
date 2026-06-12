---
title: "Can't seem to Open NAT for XBOX Live"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by deltatux on 2010-10-02
Hey guys,

I'm currently building a router out of old computer parts with Ubuntu Linux 10.04.1 LTS.

I need to do port forwarding yet only open ports I need as I'm going to double my router as a home server.

My XBOX 360 keeps saying that my NAT settings are moderate, and I can't seem for the life of me figure out how to get that to "Open".

Here's my iptables configuration script (eth0 is internal; eth1 is external; 192.168.1.20 is my XBOX 360 IP):

```

#!/bin/bash                                                                                                                                                                                                    
############################################                                                                                                                                                                   
# iptables configuration file for BANTAM   #                                                                                                                                                                   
# sets up IP forwarding and NAT forwarding #                                                                                                                                                                   
############################################                                                                                                                                                                   
                                                                                                                                                                                                               
IPTABLES=/sbin/iptables                                                                                                                                                                                        
PREROUTING="$IPTABLES -t nat -A PREROUTING"                                                                                                                                                                    
POSTROUTING="$IPTABLES -t nat -A POSTROUTING"                                                                                                                                                                  
                                                                                                                                                                                                               
sysctl -w net.ipv4.ip_forward=1                                                                                                                                                                                
                                                                                                                                                                                                               
#Flush any existing rules                                                                                                                                                                                      
$IPTABLES -F                                                                                                                                                                                                   
                                                                                                                                                                                                               
####################                                                                                                                                                                                           
#Configuring router#                                                                                                                                                                                           
####################.                                                                                                                                                                                          
$POSTROUTING -o eth1 -s 192.168.1.0/24 -j MASQUERADE                                                                                                                                                           
                                                                                                                                                                                                               
#################                                                                                                                                                                                              
#Port Forwarding#                                                                                                                                                                                              
#################

#XBOX Live
$PREROUTING -p udp --dport 88 -i eth1 -j DNAT --to 192.168.1.20
$PREROUTING -p tcp --dport 3074 -i eth1 -j DNAT --to 192.168.1.20
$PREROUTING -p udp --dport 3074 -i eth1 -j DNAT --to 192.168.1.20
$POSTROUTING -p udp -s 192.168.1.20 --sport 88 -j MASQUERADE --to-port 88
$POSTROUTING -p tcp -s 192.168.1.20 --sport 3074 -j MASQUERADE --to-port 3074
$POSTROUTING -p udp -s 192.168.1.20 --sport 3074 -j MASQUERADE --to-port 3074

######################
#Configuring firewall#
######################

#Set default policies
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT

#Allow all packets from the following interfaces:
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -j ACCEPT

#Allow the following ports to be left opened:
$IPTABLES -A INPUT -p tcp --dport 22 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p udp --dport 88 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 3074 -j ACCEPT
$IPTABLES -A INPUT -p udp --dport 3074 -j ACCEPT

#Allow packets belonging to established and related connections
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Allow port forward incoming packets
$IPTABLES -A FORWARD -p TCP -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -p UDP -m state --state ESTABLISHED,RELATED -j ACCEPT


```

Please audit and help.

Thanks,
deltatux

---

