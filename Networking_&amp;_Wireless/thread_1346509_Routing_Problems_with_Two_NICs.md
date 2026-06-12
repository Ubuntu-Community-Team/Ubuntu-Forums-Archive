---
title: "Routing Problems with Two NICs"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by moranned on 2009-12-05
Im having issues routing packets with a dual-homed server. One of the NICs is assigned an IP (10.0.1.X) by my home router and the other NIC is manually configured for a seperate LAN (192.168.1.X). My dual-homed server is also running SSH and Apache. I can connect to the SSH server from both my LAN and the Internet. However, I can connect to the Apache webserver from the 10.0.1.X LAN nor can connect to it from the Internet. However, I can connect to Apache from the 192.168.1.X LAN. I suppose this is related to my routing or iptables but am at lost to what the particular problem is.

My config is as follows:

$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:2a:b6:ae:f6  
          inet addr:192.168.1.1  Bcast:192.168.1.0  Mask:255.255.255.0
          inet6 addr: 2002:4c72:d1fb:0:214:2aff:feb6:aef6/64 Scope:Global
          inet6 addr: fe80::214:2aff:feb6:aef6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2611174 (2.6 MB)  TX bytes:1966747 (1.9 MB)
          Interrupt:20 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:22:6b:be:51:b2  
          inet addr:10.0.1.80  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4c72:d1fb:0:222:6bff:febe:51b2/64 Scope:Global
          inet6 addr: fe80::222:6bff:febe:51b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4416292 (4.4 MB)  TX bytes:3286225 (3.2 MB)
          Interrupt:21 Base address:0x6c00 

$route -n
ernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 eth1

From my Syslog

DROPPED IN=eth1 OUT= MAC=00:22:6b:be:51:b2:X:X:X:X:X:X:X:X SRC=10.0.1.25 DST=10.0.1.80 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=56396 DF PROTO=TCP SPT=49303 DPT=80 SEQ=1382543225 ACK=0 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B404020000) 

DROPPED IN=eth1 OUT= MAC=00:22:6b:be:51:b2:X:X:X:X:X:X:X:X SRC=10.0.1.25 DST=10.0.1.80 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=10775 DF PROTO=TCP SPT=49303 DPT=80 SEQ=1382543225 ACK=0 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B404020000)

---

### Post by Yoann Juet on 2009-12-05
> **moranned said:**
> Im having issues routing packets with a dual-homed server. One of the NICs is assigned an IP (10.0.1.X) by my home router and the other NIC is manually configured for a seperate LAN (192.168.1.X). My dual-homed server is also running SSH and Apache. I can connect to the SSH server from both my LAN and the Internet. However, I can connect to the Apache webserver from the 10.0.1.X LAN nor can connect to it from the Internet. However, I can connect to Apache from the 192.168.1.X LAN. I suppose this is related to my routing or iptables but am at lost to what the particular problem is.


You're right, this is related to your firewall rules. Routing is certainly ok, otherwise you would not be able to ssh into you server from internet. 

> 
From my Syslog

DROPPED IN=eth1 OUT= MAC=00:22:6b:be:51:b2:X:X:X:X:X:X:X:X SRC=10.0.1.25 DST=10.0.1.80 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=56396 DF PROTO=TCP SPT=49303 DPT=80 SEQ=1382543225 ACK=0 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B404020000) 

DROPPED IN=eth1 OUT= MAC=00:22:6b:be:51:b2:X:X:X:X:X:X:X:X SRC=10.0.1.25 DST=10.0.1.80 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=10775 DF PROTO=TCP SPT=49303 DPT=80 SEQ=1382543225 ACK=0 WINDOW=65535 RES=0x00 SYN URGP=0 OPT (020405B404020000)

HTTP connections are dropped (DPT=80, SYN) by your iptables firewall. You must add an authorization rule as showed below.

```
#iptables -A INPUT -p tcp --dport http -j ACCEPT
```

---

### Post by moranned on 2009-12-05
i updated my iptables from the command line with the following command:

$iptables -A INPUT -p tcp --dport http -j ACCEPT
this did not work. Ive list my firewall rules below for reference.

$ sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     all  --  192.168.1.1          192.168.1.0         
ACCEPT     all  --  10.0.1.80            10.0.1.255          
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    all  --  anywhere             anywhere            
srcfilt    all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
srcfilt    all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         all  --  anywhere             anywhere            

Chain f0to1 (5 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ssh state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:0:1023 dpt:ssh state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
logdrop    all  --  anywhere             anywhere            

Chain f0to2 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
logdrop    all  --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ftp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:http-alt state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:https state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:33434:33600 
logdrop    all  --  anywhere             anywhere            

Chain f1to2 (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
logdrop    all  --  anywhere             anywhere            

Chain f2to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ftp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:http-alt state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:https state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:33434:33600 
logdrop    all  --  anywhere             anywhere            

Chain f2to1 (5 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ssmtp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ftp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:http-alt state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:https state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:smtp state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
logdrop    all  --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (8 references)
target     prot opt source               destination         
logdrop2   all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
DROP       all  --  anywhere             anywhere            

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
DROP       all  --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
logdrop    all  --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      all  --  anywhere             192.168.1.1         
f0to1      all  --  anywhere             192.168.1.0         
f0to1      all  --  anywhere             10.0.1.80           
f0to1      all  --  anywhere             10.0.1.255          
f0to1      all  --  anywhere             localhost           
f0to2      all  --  anywhere             192.168.1.0/24      
logdrop    all  --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to2      all  --  anywhere             192.168.1.0/24      
f1to0      all  --  anywhere             anywhere            

Chain s2 (1 references)
target     prot opt source               destination         
f2to1      all  --  anywhere             192.168.1.1         
f2to1      all  --  anywhere             192.168.1.0         
f2to1      all  --  anywhere             10.0.1.80           
f2to1      all  --  anywhere             10.0.1.255          
f2to1      all  --  anywhere             localhost           
f2to0      all  --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s2         all  --  192.168.1.0/24       anywhere            
s0         all  --  anywhere             anywhere

---

### Post by moranned on 2009-12-05
problem is now solved. ive updated my firewall rules to accept http/https from my internal network and the internet.

thanks for pointing me in the right direction.

---

