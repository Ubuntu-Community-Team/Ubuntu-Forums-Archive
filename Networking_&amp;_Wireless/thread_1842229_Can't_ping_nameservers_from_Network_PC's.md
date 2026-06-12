---
title: "Can't ping nameservers from Network PC's"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by n8af on 2011-09-11
Hey all,

I've got a weird issue, that has me puzzled. I have my network setup so all PCs on the network go through my Ubuntu Server box, which is then connected directly to the modem.

Here is my issue.  On the Ubuntu machine, i can ping everything (network, gateway, yahoo.com, google, etc). However, when I log on my network PCs (Windows 7) I have internet, but I can't ping anything outside the network.  The windows machine can ping other computers on the network, the gateway, but not yahoo.com, google, or any nameserver.  

Things i've tried: 
Disabling my firewall
restarting bind9
rebooting both machines

I guess I don't really have an issue since my other PCs can still access the Internet.  I just find it weird that I can't ping, even with the firewall disabled.

---

### Post by Doug S on 2011-09-11
You have made good progress since yesterday.
If you post the output for "sudo iptables -v -x -n -L" on your server we should be able to trace what happens to ping packets as they go out and/or come back.

---

### Post by n8af on 2011-09-11
Chain INPUT (policy DROP 1 packets, 42 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       68.105.28.12         0.0.0.0/0           tcp flags:!0x17/0x02 
      65    18730 ACCEPT     udp  --  *      *       68.105.28.12         0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       68.105.29.12         0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       68.105.29.12         0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       68.105.28.11         0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       68.105.28.11         0.0.0.0/0           
      24     2093 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       9      756 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 1 
       3      180 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    1302  1244617 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    7517   849520 INBOUND    all  --  eth1   *       0.0.0.0/0            10.42.43.1          
       0        0 INBOUND    all  --  eth1   *       0.0.0.0/0            70.185.189.79       
     653    55733 INBOUND    all  --  eth1   *       0.0.0.0/0            10.42.43.255        
       1       42 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       1       42 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 1 
       6      360 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
     171     9224 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
    1576   464164 OUTBOUND   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
    1253   727259 ACCEPT     tcp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
     184    21512 ACCEPT     udp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.28.12        tcp dpt:53 
      65     4203 ACCEPT     udp  --  *      *       70.185.189.79        68.105.28.12        udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.29.12        tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       70.185.189.79        68.105.29.12        udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.28.11        tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       70.185.189.79        68.105.28.11        udp dpt:53 
      24     2093 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      10     2706 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
     928   168916 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    5595  2552663 OUTBOUND   all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
    pkts      bytes target     prot opt in     out     source               destination         
    8483  2003778 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       4      304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     all  --  *      *       10.42.43.31          0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.92          0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       58.218.199.250       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       58.218.199.250       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.93          0.0.0.0/0           
      36     5976 ACCEPT     all  --  *      *       10.42.43.1           0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.50          0.0.0.0/0           
     620    50437 ACCEPT     all  --  *      *       10.42.43.0/24        0.0.0.0/0           
     250    80622 ACCEPT     all  --  *      *       10.0.128.1           0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.67          0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:138 
      15     3573 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
      64     5180 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (6 references)
    pkts      bytes target     prot opt in     out     source               destination         
      73     5720 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       7      344 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       7      344 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
       9      540 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       9      540 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
      55     4644 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
      57     4836 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
    pkts      bytes target     prot opt in     out     source               destination         
      10      942 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    7625  3147957 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
      66     4450 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
     398    32394 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by n8af on 2011-09-11
> **Doug S said:**
> You have made good progress since yesterday.
If you post the output for "sudo iptables -v -x -n -L" on your server we should be able to trace what happens to ping packets as they go out and/or come back.

I'm wondering if my iptables is allowing the ping request to leave, but just not allowing it to comeback.

---

### Post by Doug S on 2011-09-11
It looks as though they get dropped. See the type 8 stuff (request) in the LSI chain.
You can help by doing an experiment, ping from your windows box and watch both the counters in the previous output and /var/log/syslog, maybe via this "grep Inbound /var/log/syslog".
Type 0 ICMP packets (reply) seem to have a path, but I only looked very quickly.

---

### Post by n8af on 2011-09-11
Do i have to edit my iptables to allow type 8 and not drop them? if so how would I do that?

---

### Post by Doug S on 2011-09-11
I would do the experiment first. The idea is to monitor the packet counters and log files to help you figure out exactly what path the ICMP packets are taking and what you want to modify. (I.E. I am being lazy and not wanting to fully understand and follow your rule set.) If the rule set is dividing into Inbound and Outbound properly, then I think my previous post might have been incorrect.
I have seen almost the same iptables on another [post]("http://ubuntuforums.org/showthread.php?t=1837905") just a few days ago. I think it is generated by some other program. Your other thread mentioned "firestarter", I think it was, so I guess that generated the rule set. Sorry, I can not help with such things, as I only write iptables rule sets directly.

---

### Post by n8af on 2011-09-11
> **Doug S said:**
>  Your other thread mentioned "firestarter", I think it was, so I guess that generated the rule set. Sorry, I can not help with such things, as I only write iptables rule sets directly.

I started out using Firestarter, then disabled it and switched to inputting the values to Iptables after reading through the security section on the Ubuntu Server guide - in hopes that it might fix my weird problem.  I'll try the experiment.

---

### Post by n8af on 2011-09-11
**Here is the last segment from the syslog after I pinged yahoo.com (69.147.125.65) from my windows machine**

Sep 11 21:07:17 (domain) kernel: [17218.400651] Inbound IN=eth1 OUT=eth0 SRC=xxx.xxx.x.22 DST=69.147.125.65 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=10724 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=2 
Sep 11 21:07:22 (domain) kernel: [17223.009825] Inbound IN=eth1 OUT=eth0 SRC=xxx.xxx.x.22 DST=69.147.125.65 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=10725 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=3 
Sep 11 21:07:27 (domain) kernel: [17228.009775] Inbound IN=eth1 OUT=eth0 SRC=xxx.xxx.x.22 DST=69.147.125.65 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=10726 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=4 
Sep 11 21:07:32 (domain) kernel: [17233.009725] Inbound IN=eth1 OUT=eth0 SRC=xxx.xxx.x.22 DST=69.147.125.65 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=10727 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=5 

**And here is the iptables:**

Chain INPUT (policy DROP 69 packets, 6330 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       68.105.28.12         0.0.0.0/0           tcp flags:!0x17/0x02 
     201    62872 ACCEPT     udp  --  *      *       68.105.28.12         0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       68.105.29.12         0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       68.105.29.12         0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       68.105.28.11         0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       68.105.28.11         0.0.0.0/0           
    1085    78485 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       9      756 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 1 
       3      180 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
     306    47173 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
      35     1580 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    6964  4626371 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
   30797  3691021 INBOUND    all  --  eth1   *       0.0.0.0/0            10.42.43.1          
       2      160 INBOUND    all  --  eth1   *       0.0.0.0/0            70.185.189.79       
   29191  2315018 INBOUND    all  --  eth1   *       0.0.0.0/0            10.42.43.255        
      69     6330 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      69     6330 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 limit: avg 1/sec burst 5 
       0        0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 code 1 
      17     1358 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   10446   539408 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
  592474 40047536 OUTBOUND   all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
 1474604 2128868925 ACCEPT     tcp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
    5517   764793 ACCEPT     udp  --  *      *       0.0.0.0/0            10.42.43.0/24       state RELATED,ESTABLISHED 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.28.12        tcp dpt:53 
     201    13057 ACCEPT     udp  --  *      *       70.185.189.79        68.105.28.12        udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.29.12        tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       70.185.189.79        68.105.29.12        udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       70.185.189.79        68.105.28.11        tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       70.185.189.79        68.105.28.11        udp dpt:53 
    1085    78485 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      10     2706 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    3052   541828 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
   26520 11741970 OUTBOUND   all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
    pkts      bytes target     prot opt in     out     source               destination         
   33821  7115646 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       4      304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     all  --  *      *       10.42.43.31          0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.92          0.0.0.0/0           
      20      800 ACCEPT     all  --  *      *       58.218.199.250       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       58.218.199.250       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.93          0.0.0.0/0           
     119    26454 ACCEPT     all  --  *      *       10.42.43.1           0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.50          0.0.0.0/0           
   29140  2298062 ACCEPT     all  --  *      *       10.42.43.0/24        0.0.0.0/0           
    3595  1165167 ACCEPT     all  --  *      *       10.0.128.1           0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.42.43.67          0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:138 
      63    15501 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
     192    10636 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (6 references)
    pkts      bytes target     prot opt in     out     source               destination         
     212    12174 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     130     5600 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
     135     5800 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
      14      840 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
      14      840 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
      61     5342 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
      63     5534 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
    pkts      bytes target     prot opt in     out     source               destination         
      76     8587 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
  609450 51427188 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    3860   362402 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    8660   533157 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by Doug S on 2011-09-11
O.K. so we can see that my earlier posting was actually correct, and you will want to delete the icmp type 8 drop rule in the LSI chain.
You can see that the packet counters increased and the log entries correspond. (I also used your other thread to know that etho and eth1 are as expected.)
You can just delete that rule from the current setup for a test. Something like (syntax may not be right):
> sudo iptables -t LSI -D -p ICMP --icmp-type echo-request -j DROPI would just leave the logging line there for now.
If you have changed to using iptables directly, then I assume you have some source file somewhere that you can edit for a permanent fix. Maybe you will want to allow outgoing ping requests from eth1 but not incoming ping requests from eth0.

---

### Post by n8af on 2011-09-11
> **Doug S said:**
> O.K. so we can see that my earlier posting was actually correct, and you will want to delete the icmp type 8 drop rule in the LSI chain.
You can see that the packet counters increased and the log entries correspond. (I also used your other thread to know that etho and eth1 are as expected.)
You can just delete that rule from the current setup for a test. Something like (syntax may not be right):
I would just leave the logging line there for now.

Awesome, i'll give it a try.

> **Doug S said:**
> 
If you have changed to using iptables directly, then I assume you have some source file somewhere that you can edit for a permanent fix. Maybe you will want to allow outgoing ping requests from eth1 but not incoming ping requests from eth0.

Do you know where I can read up on some info for configuring my iptables to do what you suggested?

---

### Post by Doug S on 2011-09-12
There are some references in the server guide referred to on that [other thread]("http://ubuntuforums.org/showthread.php?t=1841465").
Almost all of the references I have used can be found at the end of [some web notes I made]("http://www.smythies.com/~doug/network/iptables_notes/index.html") some months ago about a [packet leakage issue]("http://ubuntuforums.org/showthread.php?t=1689959"). (my own iptables rule set (a couple of versions old) is included as a link within those notes).
Of couse, since then I have learned of [bodhi.zazen's excellent notes]("http://bodhizazen.net/Tutorials/iptables/"). , with yet more references at the end.
See also the [security sticky on the Security Discussions forum ]("http://ubuntuforums.org/showthread.php?t=510812")
 
Hope this helps.

---

### Post by n8af on 2011-09-13
> **Doug S said:**
> sudo iptables -t LSI -D -p ICMP --icmp-type echo-request -j DROP 
 
 
I tried runing this line and it didn't like the "ICMP" after the "-p".  I tried doing a ip flush and clearing the iptables completely to see if I could ping with it wide open.  
The windows machine still couldn't ping.  I went back and ran iptables -L and all the rules are still there.  *scratches head*  its not letting me flush it for some reason (firestarter is disabled btw).  any ideas?

---

### Post by n8af on 2011-09-13
I figured out the problem. I think firestarter was interfering with it, even when it was disabled.  I uninstalled it and flushed the tables and it seemed to do the job. Then I added back the rules that I wanted into IPtables.  Now my network PCs can ping name addresses.

---

