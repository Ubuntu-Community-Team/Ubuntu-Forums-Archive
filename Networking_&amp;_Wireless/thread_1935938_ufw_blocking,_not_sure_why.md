---
title: "ufw blocking, not sure why"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by spezticle on 2012-03-05
from my windows box(192.168.0.2) i have a ping -t 10.0.0.2 running.
As soon as I disable ufw on the Linux box(192.168.0.1) the pings go though and stop timing out. Immediately after enabling ufw the pings time out again. 10.0.0.2/30 belongs to a Cisco router interface f0/0 within GNS3 and said Cisco router is connected to my tap0 loopback device at 10.0.0.1/30 

ufw is the only thing standing between a successful connection and i can't figure out why.

I have a static route in my hardware router pointing to the 10.0.0.0/8 subnet by way of 192.168.0.1

I am also running a tail -f on the /var/log/ufw.log
```
[ 2738.726718] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=2988 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8583 
[ 2758.726736] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=3052 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8647 
[ 2778.710632] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=3114 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8708 
[ 2798.728445] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=3178 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8772 
[ 2818.728365] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=126 ID=3246 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8836 
[ 2838.745689] [UFW BLOCK] IN=eth0 OUT=tap0 SRC=192.168.0.2 DST=10.0.0.2 LEN=60 TOS=0x00 PREC=0x00 TTL=126 ID=3310 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=8900
```

But as you can see below, i have allowed for this network
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: deny

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    10.0.0.0/8
Anywhere                   ALLOW IN    192.168.0.0/16
```

my /etc/ufw/*.rules are all defaults
i've gone through all the before.rules lines and the after.rules lines and tried disabling anything that seemed like it would block this traffic and restarted ufw each time i tried disabling or editing a new line with no success. I disabled by commenting out the line.

therefore, i assume that iptables specifically is blocking, but i'm not quite understanding why.

anyway, below is the detail of an iptables -L
maybe something in there is obvious to someone else:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh-ddos  tcp  --  anywhere             anywhere            multiport dports ssh 
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh 
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

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain fail2ban-ssh-ddos (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

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
ACCEPT     udp  --  anywhere             224.0.0.251         udp dpt:mdns 
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
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
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

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh /* 'dapp_OpenSSH' */ 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:40400 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:40400 
ACCEPT     all  --  10.0.0.0/8           anywhere            
ACCEPT     all  --  192.168.0.0/16       anywhere            

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

the attached picture shows the 4 pings running.
192.168.0.14 is my hardware router
10.0.0.1 is the tap0 device

---

