---
title: "Firestarter problem - cannot access adobe.com and others"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by yatyork on 2009-06-22
Hi all,

We're using Firestarter on Ubuntu (so much easier than Squid + iptables) and everything's working great except for the fact that we cannot access [www.adobe.com](www.adobe.com)

Strangely, forums.adobe.com is fine.

There is another website we cannot access - [www.silchester.rdg.ac.uk](www.silchester.rdg.ac.uk)

Both websites work fine when we use a machine which is not behind the Firestarter machine.

This morning I just noticed that both [www.adobe.com](www.adobe.com) and [www.silchester.rdg.ac.uk](www.silchester.rdg.ac.uk) both have IP addresses which begin with 192.x and I'm pretty certain that this has got something to do with it.

I don't know anything about iptables (and don't know a huge amount about subnet masks etc) to go in there and fix it... any ideas, guys?

---

### Post by jimv on 2009-06-22
Do you have a rule that defines any address like 192.xxx.xxx.xxx as the LAN?  Make sure that you have it set as 192.168.xxx.xxx instead.

---

### Post by yatyork on 2009-06-26
Here is a copy of the output from some iptables commands. Does this help?




gateway@ubuntu:~$ sudo iptables -nvL
[sudo] password for gateway: 
Chain INPUT (policy DROP 1 packets, 342 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       158.152.1.43         0.0.0.0/0           tcp flags:!0x17/0x02 
    2   252 ACCEPT     udp  --  *      *       158.152.1.43         0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       158.152.1.58         0.0.0.0/0           tcp flags:!0x17/0x02 
    1    76 ACCEPT     udp  --  *      *       158.152.1.58         0.0.0.0/0           
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    8   580 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            62.49.124.7         
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
   32  1024 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
  180  7271 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
  178 30458 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
  273 29906 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.1.223       
    0     0 INBOUND    all  --  eth1   *       0.0.0.0/0            62.49.124.4         
    4   916 INBOUND    all  --  eth1   *       0.0.0.0/0            192.255.255.255     
    1   342 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    1   342 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  169 85156 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
13092  657K TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
86463   11M OUTBOUND   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
 127K  116M ACCEPT     tcp  --  *      *       0.0.0.0/0            192.0.0.0/8         state RELATED,ESTABLISHED 
  681 86082 ACCEPT     udp  --  *      *       0.0.0.0/0            192.0.0.0/8         state RELATED,ESTABLISHED 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       62.49.124.4          158.152.1.43        tcp dpt:53 
    8   490 ACCEPT     udp  --  *      *       62.49.124.4          158.152.1.43        udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       62.49.124.4          158.152.1.58        tcp dpt:53 
    6   342 ACCEPgateway@ubuntu:~$ sudo iptables -nvL
[sudo] password for gateway: 
Chain INPUT (policy DROP 1 packets, 342 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       158.152.1.43         0.0.0.0/0           tcp flags:!0x17/0x02 
    2   252 ACCEPT     udp  --  *      *       158.152.1.43         0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       158.152.1.58         0.0.0.0/0           tcp flags:!0x17/0x02 
    1    76 ACCEPT     udp  --  *      *       158.152.1.58         0.0.0.0/0           
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    8   580 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            62.49.124.7         
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
   32  1024 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
  180  7271 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
  178 30458 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
  273 29906 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.1.223       
    0     0 INBOUND    all  --  eth1   *       0.0.0.0/0            62.49.124.4         
    4   916 INBOUND    all  --  eth1   *       0.0.0.0/0            192.255.255.255     
    1   342 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    1   342 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  169 85156 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
13092  657K TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
86463   11M OUTBOUND   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
 127K  116M ACCEPT     tcp  --  *      *       0.0.0.0/0            192.0.0.0/8         state RELATED,ESTABLISHED 
  681 86082 ACCEPT     udp  --  *      *       0.0.0.0/0            192.0.0.0/8         state RELATED,ESTABLISHED 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       62.49.124.4          158.152.1.43        tcp dpt:53 
    8   490 ACCEPT     udp  --  *      *       62.49.124.4          158.152.1.43        udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       62.49.124.4          158.152.1.58        tcp dpt:53 
    6   342 ACCEPT     udp  --  *      *       62.49.124.4          158.152.1.58        udp dpt:53 
    9  2371 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   16  2151 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
   88  6944 OUTBOUND   all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
 pkts bytes target     prot opt in     out     source               destination         
   10  1385 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    4   304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  441 59591 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
  441 59591 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    8   416 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    8   416 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
  433 59175 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
  433 59175 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
 pkts bytes target     prot opt in     out     source               destination         
   88  6944 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
78450   11M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  120  9897 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 7909  591K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
gateway@ubuntu:~$ sudo iptables -nvL -t nat
Chain PREROUTING (policy ACCEPT 9907 packets, 646K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 16 packets, 816 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 8042  452K MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 17 packets, 985 bytes)
 pkts bytes target     prot opt in     out     source               destination         
T     udp  --  *      *       62.49.124.4          158.152.1.58        udp dpt:53 
    9  2371 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   16  2151 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
   88  6944 OUTBOUND   all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
 pkts bytes target     prot opt in     out     source               destination         
   10  1385 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    4   304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  441 59591 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
  441 59591 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    8   416 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    8   416 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
  433 59175 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
  433 59175 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
 pkts bytes target     prot opt in     out     source               destination         
   88  6944 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
78450   11M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  120  9897 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 7909  591K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
gateway@ubuntu:~$ sudo iptables -nvL -t nat
Chain PREROUTING (policy ACCEPT 9907 packets, 646K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 16 packets, 816 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 8042  452K MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 17 packets, 985 bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by yatyork on 2009-06-26
> **yatyork said:**
> 
          
  273 29906 INBOUND    all  --  eth1   *       0.0.0.0/0            192.168.1.223       
    0     0 INBOUND    all  --  eth1   *       0.0.0.0/0            62.49.124.4         
    **4   916 INBOUND    all  --  eth1   *       0.0.0.0/0            192.255.255.255**     
    

Could it be this one?

---

### Post by yatyork on 2009-06-30
Anyone?

---

