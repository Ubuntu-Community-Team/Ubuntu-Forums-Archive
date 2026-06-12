---
title: "Ubuntu as NAT, can't connect from LAN to server"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by jlaurika on 2011-04-03
Problem is that i've got:
INET -> eth0 (DHCP) Ubuntu 10.04 eth1 (192.168.0.1) -> comp1 192.168.0.2
                                                    -> comp2 192.168.0.3

All computers in LAN can connect to INET just fine. But I cannot connect to Ubuntu box at all. I got murmur server running in Ubuntu, everybody from outside can connect but none from inside. (not with eth0 or eth1 ip/dns).

All pings/connections from 192.168.0.2 are ignored to 192.168.0.1

I followed guide from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) and for now did just basic static IP:s. So how do I allow all connections from 192.168.0.X to my ubuntu?

PS. 64738 udp/tcp is murmur/mumble port. iptables is bit messy since I used firestarter to generate it.

**netstat -rn**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Ifac
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
80.221.48.0     0.0.0.0         255.255.248.0   U         0 0          0 eth0
0.0.0.0         80.221.48.1     0.0.0.0         UG        0 0          0 eth0
**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
80.221.48.0     0.0.0.0         255.255.248.0   U     1      0        0 eth0
0.0.0.0         80.221.48.1     0.0.0.0         UG    0      0        0 eth0


Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  ns.inet.fi           anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns.inet.fi           anywhere            
ACCEPT     tcp  --  ns7.inet.fi          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns7.inet.fi          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             80.221.55.255       
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
ACCEPT     all  --  192.168.0.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  hoasnet-fe37dd00-118.dhcp.inet.fi  ns.inet.fi          tcp dpt:domain 
ACCEPT     udp  --  hoasnet-fe37dd00-118.dhcp.inet.fi  ns.inet.fi          udp dpt:domain 
ACCEPT     tcp  --  hoasnet-fe37dd00-118.dhcp.inet.fi  ns7.inet.fi         tcp dpt:domain 
ACCEPT     udp  --  hoasnet-fe37dd00-118.dhcp.inet.fi  ns7.inet.fi         udp dpt:domain 
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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:64738 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:64738 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:19558 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:19558 
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

---

