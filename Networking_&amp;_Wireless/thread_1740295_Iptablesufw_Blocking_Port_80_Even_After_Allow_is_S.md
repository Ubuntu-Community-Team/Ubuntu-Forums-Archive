---
title: "Iptables/ufw Blocking Port 80 Even After Allow is Set"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by hyetech on 2011-04-26
I'm running ufw/iptables on ubuntu server 9.10 and have little experience with iptables.  I have set ufw to allow port 80 and other ports.  Most of the time, everything works, but watching /var/log/messages, I still see a UFW block of that port and I am not sure why.  What am I missing?  I had a similar issue with firehol, so I turned that off and used ufw instead.

Here are samples from /var/log/messages:
```
Apr 26 17:26:17 crm kernel: [UFW BLOCK] IN=eth0 OUT= MAC=fe:fd:ad:e6:95:50:c8:4c:75:f5:d6:3f:08:00 SRC=200.4.167.81 DST=173.230.149.80 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=17888 DF PROTO=TCP SPT=1900 DPT=80 WINDOW=64364 RES=0x00 ACK FIN URGP=0 
Apr 26 17:26:17 crm kernel: [UFW BLOCK] IN=eth0 OUT= MAC=fe:fd:ad:e6:95:50:c8:4c:75:f5:d6:3f:08:00 SRC=200.4.167.81 DST=173.230.149.80 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=17889 DF PROTO=TCP SPT=61275 DPT=80 WINDOW=64500 RES=0x00 ACK FIN URGP=0 

```

Here is output from "ufw status verbose":
```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
3306                       ALLOW IN    Anywhere
8090                       ALLOW IN    Anywhere
3128                       ALLOW IN    Anywhere
17500                      ALLOW IN    Anywhere
80/tcp (Apache)            ALLOW IN    Anywhere
22/tcp (OpenSSH)           ALLOW IN    Anywhere
123                        ALLOW IN    Anywhere

```

Here is iptables -L if it helps (none of which I modified myself):
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:mysql 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8090 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8090 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3128 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:3128 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:17500 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:17500 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www /* 'dapp_Apache' */ 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh /* 'dapp_OpenSSH' */ 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         

```

---

### Post by Doug S on 2011-04-26
Those packets are asking for the TCP connection to be terminated (the ACK and FIN bits are set). My guess is that the TCP connection was already closed with a previous ACK FIN packet or some other method and that the contrack table has forgotten about it. A new WWW TCP session can only be started with the SYN bit set and FIN, RST, ACK reset.
 
There was a very similar thread to this not long ago, and it ended up with many links to good references about TCP sessions and the flag bits and such. I couldn't find it just now, but I will edit in a link if I can find it later.
[http://ubuntuforums.org/showthread.php?t=1729742](http://ubuntuforums.org/showthread.php?t=1729742)

---

### Post by hyetech on 2011-04-27
Doug, thanks so much for the explanation and thread link - that helps.  From what you and the thread are saying, unless I see a block with the SYN bit set, these can be ignored in a sense as they aren't blocking folks from using the website.  Please correct me if I'm wrong in that thinking.

Given that, is there a way to filter these types of blocks out of the log?  Just so we're not confused by seeing them?

---

### Post by Doug S on 2011-04-27
Yes, Those packets can be ignored and they are not preventing users from accessing your web site.
You should be able to not log such events. I do not use ufw, so can not help with how. I will say, though, that myself I like to have all such events logged.

---

