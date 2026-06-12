---
title: "enabling non-internet LAN makes internet over wireless stop working"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by admalledd on 2010-09-01
I am trying to connect my desktop to my laptop over a non-internet connected LAN, but when i enable the LAN connection on my desktop (the one with the wireless) its internet stops working.

it is a very similar problem to [_this_]("http://superuser.com/questions/48898/inserting-a-non-internet-lan-cable-breaks-wifi") except that i am using ubuntu for the machine with the two connections. 

right now i have my wireless on the 192.168.1.* address space, while the LAN is to be on 192.168.5.*

note: my goal is not to share internet with my laptop, just be able to connect to it and the internet at the same time.

desktop: ubuntu 9.10 , wireless and LAN
laptop: windows xp, LAN only

---

### Post by Iowan on 2010-09-01
Check **route -n**. I suspect the "gateway" is shifting to the non-internet" interface (eth0?). Network Manager *should* be able to adjust the settings - you can set up a route on the wireless, and have the other one "use this connection only for resources on its network".

---

### Post by admalledd on 2010-09-01
i found the routing settings, but what route would i enter for the wireless? the LAN?

after checking (on the LAN eth0) "use this connection only for resources on its network" i have internet again, but now when i ping the LAN hub i get:
```
$ ping 192.168.5.1
PING 192.168.5.1 (192.168.5.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
--- 192.168.5.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms


```

---

### Post by BkkBonanza on 2010-09-01
"Operation not permitted" probably means you need root permissions. Try **sudo ping** ...

---

### Post by Iowan on 2010-09-01
A quick search on the error message suggested root permissions or **iptables** as the culprit. You can check **iptables -L** to see if any rules are present - if so, that previous change might have done it. :confused: (Machine *shouldn't* require **sudo** for ping, but try it...)

---

### Post by admalledd on 2010-09-01
well, "sudo ping" did the same thing, and i have yet to understand much about iptables, so here is a dump from the command...
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     tcp  --  192.168.5.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.5.1          anywhere            
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
ACCEPT     tcp  --  192.168.1.101        192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        192.168.1.1         udp dpt:domain 
ACCEPT     tcp  --  192.168.1.101        192.168.5.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        192.168.5.1         udp dpt:domain 
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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5900 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5900 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6600 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6600 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8000 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:2200:2400 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:2200:2400 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6111 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6111 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6112 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6112 
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

---

### Post by BkkBonanza on 2010-09-01
Without scrutinizing that too carefully it seems you may have a reject on icmp outbound there. I'd suggest briefly flushing iptables, testing and then reloading. Or if your'e using ufw (or another firewall) then briefly disable it and test.

---

### Post by admalledd on 2010-09-02
aparently, my firewall (firestarter which I use to open ports for gaming) decides to block things from that LAN interface. weird. when i connect, and then press "disable firewall" (the big red button at top) i am able to ping away and connect to both networks. thank you!

recap for future people: go into network manager, select your "lan" connection, go to ipv4 settings, click on routes, check the box that says "use this connection only for resources on its network"

also: make sure you don't have a firewall trying to "protect" you incorrectly. for me, firestarter thought that my LAN was the open internet and got paranoid, blocking my connections.

---

### Post by BkkBonanza on 2010-09-02
While it's been years since I used Firestarter, so I couldn't say exactly how, there is probably a way to add a rule that allows traffic for the LAN ip range while keeping others blocked. This would be preferable to disabling the firewall completely.

---

### Post by admalledd on 2010-09-02
for me, i am making this be my force making me need to learn more about iptables, and how to use it.

---

