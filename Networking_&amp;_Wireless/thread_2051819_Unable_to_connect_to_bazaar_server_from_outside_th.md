---
title: "Unable to connect to bazaar server from outside the LAN"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by vichor on 2012-09-02
Hi all,

I have a small bzr server at home, just for fun. Using different computers in my home LAN, I can connect to this server without any problem. I want, though, to be able to connect from other places, such as my parents' home and so. I failed at this so far...

I have dynamic IP assignation from my ISP, so the first step was getting the IP each time it was changing. I have  managed to build up a script which emails me my public IP address, so I would be able to connect to my bzr server from outside my LAN.

I have also opened in my router the 4155 port where bzr server is placed. I have opened the port using the web interface, as I have no knowledge of iptables to play up directly with them. 

But after all this, my router is refusing the connection to the server. This is what wireshark is capturing (something called K12 format):

```

+---------+---------------+----------+
10:54:57,198,859   ETHER
|0   |30|39|f2|73|f3|2d|00|02|6f|81|52|ed|08|00|45|00|00|3c|64|e4|40|00|40|06|b5|48|c0|a8|01|6f|c1|99|9c|de|a2|46|10|3b|b2|b7|62|2e|00|00|00|00|a0|02|39|08|20|be|00|00|02|04|05|b4|04|02|08|0a|00|0a|06|ca|00|00|00|00|01|03|03|04|

+---------+---------------+----------+
10:54:57,200,356   ETHER
|0   |00|02|6f|81|52|ed|30|39|f2|73|f3|2d|08|00|45|00|00|28|00|00|40|00|40|06|1a|41|c1|99|9c|de|c0|a8|01|6f|10|3b|a2|46|00|00|00|00|b2|b7|62|2f|50|14|00|00|c7|d8|00|00|

```

So far, I do not know what else I can do, so if anybody here tells me what is wrong, I would be grateful.

Below are my iptables config:

```
# iptables -nvL
Chain INPUT (policy ACCEPT 558 packets, 128K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     icmp --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
  103 17284 ACCEPT     all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:7547 
    3   144 LOG        tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 6/hour burst 5 LOG flags 0 level 1 prefix `Intrusion -> ' 
    3   144 DROP       all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 467 packets, 79143 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   86  5120 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
  434  317K USERFORWARD  all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
  434  317K ACCEPT     all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 LOG        tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 6/hour burst 5 LOG flags 0 level 1 prefix `Intrusion -> ' 
    0     0 DROP       all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 647 packets, 207K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      ppp1    0.0.0.0/0            239.255.255.250     
    0     0 DROP       all  --  *      ppp0    0.0.0.0/0            239.255.255.250     

Chain USERFORWARD (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.45.0/24       0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       172.20.25.0/24       0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       80.58.63.128/25      0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:23 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  ppp0   *       193.152.37.192/28    0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     icmp --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.111       udp dpt:4155 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.111       tcp dpt:4155 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.43        tcp dpt:53 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.43        udp dpt:53 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.43        tcp dpt:88 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.43        udp dpt:88 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.43        tcp dpt:3074 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.43        udp dpt:3074 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.111       tcp dpt:4662 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.111       udp dpt:4672 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.111       tcp dpts:6881:6999 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.168.1.111       tcp dpt:51413 
    0     0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.168.1.111       udp dpt:51413 

```
```
# iptables -nvL -t nat
Chain PREROUTING (policy ACCEPT 145 packets, 16472 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:7547 
  163 17587 CAPTIVE_PORTAL  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:51413 to:192.168.1.111 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:51413 to:192.168.1.111 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6999 to:192.168.1.111 
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:4672 to:192.168.1.111 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:4662 to:192.168.1.111 
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:3074 to:192.168.1.43 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:3074 to:192.168.1.43 
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:88 to:192.168.1.43 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:88 to:192.168.1.43 
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 to:192.168.1.43 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 to:192.168.1.43 
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:4155 to:192.168.1.111 
    0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:4155 to:192.168.1.111 

Chain POSTROUTING (policy ACCEPT 18 packets, 2218 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   45  5092 MASQUERADE  all  --  *      ppp0    192.168.1.0/24       0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 18 packets, 2218 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain CAPTIVE_PORTAL (1 references)
 pkts bytes target     prot opt in     out     source               destination
```

My router claims to be a BCM96328 Broadband Router, just in case this info is needed.

Thanks!!

---

### Post by 2F4U on 2012-09-02
Did you configure port forwarding on your router? If you connect to the router on a particular port it doesn't know what to do with this request. The port 4155 is on the server, but when you come from outside you connect to your router. You have to tell the router that when someone accesses the port 4155 this request should be forwarded to the server. As far as i know, the server must have a static IP for that to work.

---

### Post by vichor on 2012-09-02
Hey, thanks for passing by and dedicate some time to answer!

Yes, port forwarding is there, at least as far as I know:

```

(extracted from my original post)
0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:4155 to:192.168.1.111 
0     0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:4155 to:192.168.1.111 

```

And also the port is configured to allow connection in the ACCEPT (chain?).

About static vs dynamic IP, I guess that it is needed static if you want a server for lots of people to access it, mostly because if the IP is changing from time to time, it would be a chaos to be updating this constantly in all DNSes and so... but I just want to sporadically connect, and I know beforehand my assigned IP.

Well in my iptables I see everything OK, but the connection is refused (so not everything is correct, eh?). If the must of having static IP is confirmed, then I will stop trying this.

---

