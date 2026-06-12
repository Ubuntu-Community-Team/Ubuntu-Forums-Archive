---
title: "Apache Working on Local Machine, But Not on LAN"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by dseldentreiman on 2009-04-29
I have an Apache 2.2.11 Server running on Ubuntu 9.04.  I am able to access this server locally through 127.0.0.1, however not over Ethernet.

I receive an active ping from the server through the client computer, however I am not able to access the Apache server.  I do not have any firewalls running, such as Firestarter, so I cannot place the problem there.

Any Suggestions?

Thank you in advance.

---

### Post by dmizer on 2009-04-29
When attempting to access your site over your LAN, are you typing the server's LAN IP, or your WAN IP?

Many consumer end routers are not capable of loopback, which means that you'll have to use the server's local IP to access your site while inside your LAN.

If you are using the LAN IP, then you may have a firewall problem. Please post the output of:
```
sudo iptables -L
```

---

### Post by dseldentreiman on 2009-04-29
I believe that am typing in the LAN IP (169.254.*.*)...

Here is the IP Table Dump
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  resolver1.opendns.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  resolver1.opendns.com  anywhere            
ACCEPT     tcp  --  resolver2.opendns.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  resolver2.opendns.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             169.254.0.101       
INBOUND    all  --  anywhere             192.168.1.201       
INBOUND    all  --  anywhere             169.254.255.255     
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             link-local/16       state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             link-local/16       state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.201        resolver1.opendns.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.201        resolver1.opendns.com udp dpt:domain 
ACCEPT     tcp  --  192.168.1.201        resolver2.opendns.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.201        resolver2.opendns.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.119        anywhere            
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere      

Thank you for the quick response!

~David

---

### Post by dmizer on 2009-04-29
169.254.x.x is Automatic Private IP Addressing. It's a locally assigned IP address and no traffic is sent to that IP. Your server IP address would be 192.168.1.x or 192.168.0.x (192.168.0.119 perhaps? Can't tell for sure).

I don't see a rule in your IPtables configuration for pointing port 80 to local host. It looks to me like you're forwarding all packets between the 192.168.1.x and 192.168.0.x, perhaps for internet connection sharing? I'm not very familiar with IPtables routing, but if you can't view your page by typing your server's actual IP address, you'll need to look at your IPtables configuration.

---

### Post by dseldentreiman on 2009-04-30
Thanks for the pointer!

I flushed my iptables...
[http://ubuntuforums.org/showthread.php?t=217085](http://ubuntuforums.org/showthread.php?t=217085)

and reconfigured...
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

and it worked!!!

Thank you for your help

~David

---

### Post by dmizer on 2009-04-30
Fantastic!

---

