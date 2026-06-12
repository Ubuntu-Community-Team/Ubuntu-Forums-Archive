---
title: "[SOLVED] Internet Gateway"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by BUNAC on 2008-12-03
Hi guys,
Can someone let me know where I'm going wrong!??

I'm trying to set up an Internet Gateway by following the examples on here and at: 
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

This is my set up:

Internet <<==>> eth1 (192.168.1.50)<> Ubuntu gateway <> eth0 (192.168.0.210)<<==>> Client PC 

The client PC has the following static setup
IP:               192.168.0.78
Subnet Mask:      255.255.0.0
Default Gateway:  192.168.0.210

I have followed the instructions to enable IP forwarding but I can't get passed the Gateway! The client PC can ping eth0 and the gateway can get out to the internet. Unfortunately the client PC can't access the internet so I must have made an error with the forwarding.

Can anyone help me, please? :D

---

### Post by s3gfault on 2008-12-03
The error is most likely in your iptables script.  Post that please, i'll provide any help i can.

---

### Post by BUNAC on 2008-12-03
Hello s3gfault,
First off apologies I'm a complete noob to Linux!

I used the command "sudo iptables -L" to list the rules shown below:

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.3          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.3          anywhere            
ACCEPT     tcp  --  192.168.1.4          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.4          anywhere            
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.210       
INBOUND    all  --  anywhere             192.168.1.50        
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.50         192.168.1.3         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.50         192.168.1.3         udp dpt:domain 
ACCEPT     tcp  --  192.168.1.50         192.168.1.4         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.50         192.168.1.4         udp dpt:domain 
ACCEPT     tcp  --  192.168.1.50         192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.50         192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  224.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.0/8         
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

This seems like a huge amount of rules to me! Especially as for the moment I just want to let all traffic through. Any suggestions would be appreciated!?

---

### Post by superprash2003 on 2008-12-03
well.. i think iptables may have been messed up.. Do this , flush your iptables [http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html) and then setup internet connection sharing by either using firestarter ( sudo apt-get install firestarter)  or manually by this link [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by BUNAC on 2008-12-10
After a lot of fiddling and correcting a few stupid mistakes this is up and running. Thanks superprash2003 :KS

---

