---
title: "Firewall (Firestarter) issue."
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-05-06
I am running 10.04. I have 2 network cards eth0, and wlan0, and Firestarter is providing my firewall.

My understanding of Firestarter, is that it reads it's config files and applies IPTABLES commands to create the firewall.

eth0 is my internet connection, and works fine on 192.168.1.97. I have told Firestarter to allow all connections from 192.168.1.0/24 which works great. So can access my machine if I connect to my internet router.

wlan0 is configured to be 192.168.2.12. I have also told Firestarter to allow all connections from 192.168.2.0/24. However, it seems to ignore this. The wlan0 connection can't send or receive traffic.

running IPTABLES -L after Firestarter has loaded shows this 

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     tcp  --  cache1.service.virginmedia.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cache1.service.virginmedia.net  anywhere            
ACCEPT     tcp  --  cache2.service.virginmedia.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cache2.service.virginmedia.net  anywhere            
ACCEPT     tcp  --  192.168.2.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.2.1          anywhere            
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
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.97         192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.97         192.168.1.1         udp dpt:domain 
ACCEPT     tcp  --  192.168.1.97         cache1.service.virginmedia.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.97         cache1.service.virginmedia.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.97         cache2.service.virginmedia.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.97         cache2.service.virginmedia.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.97         192.168.2.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.97         192.168.2.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.1.0/24       anywhere            
ACCEPT     all  --  10.20.30.0/24        anywhere            
ACCEPT     all  --  192.168.2.0/24       anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:36902 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:36902 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:971 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:971 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:10097 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:10097 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6886 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6886 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51413 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51413 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8765 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8765 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1723 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1723 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:fsp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9091 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9091 
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

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere        
```

Now I am not a IPTABLES guru, but I suspect that the basic rule which prevents all in/out traffic is being applied out of order, so that the command to allow traffic (which I can see above) is superceded. Can anyone help ?

Is this a bug or feature in Firestarter ?

---

