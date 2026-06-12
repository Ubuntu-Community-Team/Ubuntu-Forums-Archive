---
title: "DNS and KVM, urg!!!"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by FORCED-INDUCTN on 2009-05-08
Hello, I have a developed a very annoying network issue. Ever since I installed KVM and all its virtualizaion packages, and set up to VPSs I cannot ping a domain. For example I can ping my gateway:

ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.443 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.452 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.420 ms
^C
--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.420/0.438/0.452/0.021 ms

But if I try to ping a domain like [www.google.com](www.google.com) I get this:

ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.155.104) 56(84) bytes of data.
From 192.168.2.120 icmp_seq=1 Destination Port Unreachable
From 192.168.2.120 icmp_seq=2 Destination Port Unreachable
From 192.168.2.120 icmp_seq=3 Destination Port Unreachable
^CFrom 192.168.2.120 icmp_seq=4 Destination Port Unreachable

However my web browser on the server still works just fine, and so does apt-get update and installing packages. But I cant install anything in the VPSs because the cant resolve domain names apparently, I thought this was a problem with KVM but its affecting the whole server. I think it has to do with iptables (duh) because when I run iptables -F (I think thats what it is) which ive heard disable iptables, then I can ping domains from the server but then of course the VPSs lose all connectivity because iptables does the routing to and from the VPS and the host machine.

Hear is my iptables stuff, hopefully this helps and if you need more info feel free to ask :) thanx in advance!

iptables stuff:

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
blockcontrol_in  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
blockcontrol_fw  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
blockcontrol_out  all  --  anywhere             anywhere            state NEW mark match !0x14 

Chain blockcontrol_fw (1 references)
target     prot opt source               destination         
RETURN     all  --  192.168.122.0/24     192.168.122.0/24    
DROP       all  --  anywhere             anywhere            mark match 0xa 
RETURN     all  --  anywhere             dnsr2.sbcglobal.net 
RETURN     all  --  anywhere             dnsr1.sbcglobal.net 
RETURN     all  --  anywhere             192.168.2.1         
RETURN     all  --  anywhere             192.168.122.1       
RETURN     all  --  192.168.2.0/24       192.168.2.0/24      
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain blockcontrol_in (1 references)
target     prot opt source               destination         
RETURN     all  --  192.168.122.0/24     anywhere            
DROP       all  --  anywhere             anywhere            mark match 0xa 
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  192.168.2.0/24       anywhere            
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

Chain blockcontrol_out (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             192.168.122.0/24    
REJECT     all  --  anywhere             anywhere            mark match 0xa reject-with icmp-port-unreachable 
RETURN     all  --  anywhere             dnsr2.sbcglobal.net 
RETURN     all  --  anywhere             dnsr1.sbcglobal.net 
RETURN     all  --  anywhere             192.168.2.1         
RETURN     all  --  anywhere             192.168.122.1       
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             192.168.2.0/24      
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:https 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 92

---

