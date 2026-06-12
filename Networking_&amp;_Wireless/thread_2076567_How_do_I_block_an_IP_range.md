---
title: "How do I block an IP range ?"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by cogset on 2012-10-26
I want to block some IPs (deny them from accessing my computer and block everything from my computer to those IPs),what's the best way to do it?
I take that the /etc/hosts file only works with actual domain names,not IPs,and wouldn't accept an IP range anyways,is that correct?
I've added the IP range I want to block to ufw already,the rules have been added but then,when I look for connections with ss,the IP in question has a connection established nonetheless:what am I doing wrong ?
If a program I have installed needs that connection,will it override the firewall settings ? I think it shouldn't,maybe I am overlooking something,as I know nothing about iptables and can barely add rules to ufw ?

---

### Post by 2F4U on 2012-10-26
Maybe you should tell us how you configured ufw. Here are nice examples on how to configure ufw. Note that ufw is not enabled by default and has to be enabled explicitly.

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by vandorjw on 2012-10-26
post 
```

sudo iptables -L

```

---

### Post by cogset on 2012-10-26
I guess that below is the significant part from iptables

```
Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 
DROP       udp  --  anywhere             anywhere            udp dpt:ssh 
DROP       tcp  --  212.48.8.140         ubuntu-desktop.local 
DROP       udp  --  212.48.8.140         ubuntu-desktop.local 
DROP       tcp  --  vps13662.ovh.net     ubuntu-desktop.local 
DROP       udp  --  vps13662.ovh.net     ubuntu-desktop.local 
DROP       all  --  212.48.8.140         ubuntu-desktop.local 
DROP       tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp dpt:nfs 
DROP       udp  --  anywhere             anywhere            udp dpt:nfs 
DROP       tcp  --  anywhere             anywhere            tcp dpt:7634 
DROP       udp  --  anywhere             anywhere            udp dpt:7634 
DROP       all  --  111.221.64.0/111.221.127.255  anywhere            
DROP       all  --  213.199.160.0/213.199.191.255  anywhere            
DROP       all  --  157.52.0.0/157.60.255.255  anywhere            
DROP       all  --  65.52.0.0/65.55.255.255  anywhere            
DROP       all  --  207.46.0.0/207.46.255.255  anywhere            
DROP       all  --  anywhere             207.46.0.0/207.46.255.255 
DROP       all  --  2.192.0.0/2.195.255.255  anywhere            
DROP       all  --  anywhere             2.192.0.0/2.195.255.255 
DROP       all  --  212.48.8.0/212.48.11.255  anywhere            
DROP       all  --  anywhere             212.48.8.0/212.48.11.255 
DROP       all  --  anywhere             151.75.0.0/151.75.255.255 
DROP       all  --  151.75.0.0/151.75.255.255  anywhere            
DROP       all  --  ip-78-141-128-0.dyn.luxdsl.pt.lu/78.141.191.255  anywhere            
DROP       all  --  anywhere             ip-78-141-128-0.dyn.luxdsl.pt.lu/78.141.191.255 
DROP       all  --  host204-13-162-127.oversee.net  anywhere            
DROP       all  --  anywhere             host204-13-162-127.oversee.net 
DROP       all  --  98.142.96.0/98.142.111.255  anywhere            
DROP       all  --  anywhere             98.142.96.0/98.142.111.255 
DROP       all  --  anywhere             host204-13-160-0.oversee.net/204.13.163.255 
DROP       all  --  host204-13-160-0.oversee.net/204.13.163.255  anywhere            
DROP       all  --  208.73.208.0/208.73.215.255  anywhere            
DROP       all  --  anywhere             208.73.208.0/208.73.215.255 
DROP       all  --  anywhere             213.135.251.0/213.135.251.255 
DROP       all  --  213.135.251.0/213.135.251.255  anywhere            
DROP       all  --  54.240.0.0/54.255.255.255  anywhere            
DROP       all  --  anywhere             54.240.0.0/54.255.255.255 
DROP       all  --  anywhere             ec2-23-20-0-0.compute-1.amazonaws.com/23.23.255.255 
DROP       all  --  ec2-23-20-0-0.compute-1.amazonaws.com/23.23.255.255  anywhere            
DROP       all  --  216.182.224.0/216.182.239.255  anywhere            
DROP       all  --  anywhere             216.182.224.0/216.182.239.255 
DROP       all  --  anywhere             213.199.160.0/213.199.191.255 


Chain ufw-user-output (1 references)
target     prot opt source               destination         
DROP       all  --  ubuntu-desktop.local  212.48.8.140        
DROP       tcp  --  ubuntu-desktop.local  212.48.8.140        
DROP       udp  --  ubuntu-desktop.local  212.48.8.140        
DROP       tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp dpt:nfs 
DROP       udp  --  anywhere             anywhere            udp dpt:nfs 
DROP       tcp  --  anywhere             anywhere            tcp dpt:7634 
DROP       udp  --  anywhere             anywhere            udp dpt:7634 
DROP       all  --  anywhere             111.221.64.0/111.221.127.255 
DROP       all  --  anywhere             213.199.160.0/213.199.191.255 
DROP       all  --  anywhere             157.52.0.0/157.60.255.255 
DROP       all  --  anywhere             65.52.0.0/65.55.255.255 
DROP       all  --  anywhere             2.192.0.0/2.195.255.255 



```what I would like to understand is why,for instance,whilst the
213.199.160.0/213.199.191.255 range is apparently denied access by ufw (that's what I think,at the least) nonetheless when using skype an https connection to such IP is active,despite the fact that not only such program should only  use port 21722 ,other connections should be blocked by the firewall anyways.

---

### Post by Doug S on 2012-10-26
My guess it that there is a path around what you have shown. Even though I find ufw generated iptables hard to read, please show us the complete output from:```
sudo iptables -v -x -n -L
```Is this computer also a router? If yes, please include:```
sudo iptables -t nat -v -x -n -L
```

---

### Post by cogset on 2012-10-26
OK,so this is the complete output of iptables -L

```
 sudo iptables -L

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
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

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
ACCEPT     all  --  base-address.mcast.net/4  anywhere            
ACCEPT     all  --  anywhere             base-address.mcast.net/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

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
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 
DROP       udp  --  anywhere             anywhere            udp dpt:ssh 
DROP       tcp  --  212.48.8.140         ubuntu-desktop.local 
DROP       udp  --  212.48.8.140         ubuntu-desktop.local 
DROP       tcp  --  vps13662.ovh.net     ubuntu-desktop.local 
DROP       udp  --  vps13662.ovh.net     ubuntu-desktop.local 
DROP       all  --  212.48.8.140         ubuntu-desktop.local 
DROP       tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
DROP       udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp dpt:nfs 
DROP       udp  --  anywhere             anywhere            udp dpt:nfs 
DROP       tcp  --  anywhere             anywhere            tcp dpt:7634 
DROP       udp  --  anywhere             anywhere            udp dpt:7634 
DROP       all  --  111.221.64.0/111.221.127.255  anywhere            
DROP       all  --  213.199.160.0/213.199.191.255  anywhere            
DROP       all  --  157.52.0.0/157.60.255.255  anywhere            
DROP       all  --  65.52.0.0/65.55.255.255  anywhere            
DROP       all  --  207.46.0.0/207.46.255.255  anywhere            
DROP       all  --  anywhere             207.46.0.0/207.46.255.255 
DROP       all  --  2.192.0.0/2.195.255.255  anywhere            
DROP       all  --  anywhere             2.192.0.0/2.195.255.255 
DROP       all  --  212.48.8.0/212.48.11.255  anywhere            
DROP       all  --  anywhere             212.48.8.0/212.48.11.255 
DROP       all  --  anywhere             151.75.0.0/151.75.255.255 


```and this is for iptables -v -x -n -L
```
 sudo iptables -v -x -n -L

Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    4247  4009413 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4247  4009413 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       8     4608 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 2 packets, 80 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    3714   331495 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    3714   331495 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     695    47240 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     695    47240 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     695    47240 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     695    47240 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
       8     4608 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
       0        0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      60     5038 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     150    10132 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    3835  3954492 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       1       40 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       1       40 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
       2     1152 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
     259    43597 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
     226    35859 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
      33     7738 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      62     8023 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      64     4929 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     150    10132 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    2869   274123 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
     695    47240 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       1       40 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
     226    35859 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
      33     7738 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
    pkts      bytes target     prot opt in     out     source               destination         
       8     4608 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     160     9600 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
     533    37560 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:22 
       0        0 DROP       tcp  --  *      *       212.48.8.140         192.168.1.215       
       0        0 DROP       udp  --  *      *       212.48.8.140         192.168.1.215       
       0        0 DROP       tcp  --  *      *       46.105.8.220         192.168.1.215       
       0        0 DROP       udp  --  *      *       46.105.8.220         192.168.1.215       
       0        0 DROP       all  --  *      *       212.48.8.140         192.168.1.215       
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445 
      25     3130 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 137,138 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:7634 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:7634 
       0        0 DROP       all  --  *      *       111.221.64.0/111.221.127.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       213.199.160.0/213.199.191.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       157.52.0.0/157.60.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       65.52.0.0/65.55.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       207.46.0.0/207.46.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            207.46.0.0/207.46.255.255 
       0        0 DROP       all  --  *      *       2.192.0.0/2.195.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            2.192.0.0/2.195.255.255 
       0        0 DROP       all  --  *      *       212.48.8.0/212.48.11.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            212.48.8.0/212.48.11.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            151.75.0.0/151.75.255.255 
       0        0 DROP       all  --  *      *       151.75.0.0/151.75.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       78.141.128.0/78.141.191.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            78.141.128.0/78.141.191.255 
       0        0 DROP       all  --  *      *       204.13.162.127       0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            204.13.162.127      
       0        0 DROP       all  --  *      *       98.142.96.0/98.142.111.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            98.142.96.0/98.142.111.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            204.13.160.0/204.13.163.255 
       0        0 DROP       all  --  *      *       204.13.160.0/204.13.163.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       208.73.208.0/208.73.215.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            208.73.208.0/208.73.215.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            213.135.251.0/213.135.251.255 
       0        0 DROP       all  --  *      *       213.135.251.0/213.135.251.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       54.240.0.0/54.255.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            54.240.0.0/54.255.255.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            23.20.0.0/23.23.255.255 
       0        0 DROP       all  --  *      *       23.20.0.0/23.23.255.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       216.182.224.0/216.182.239.255  0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            216.182.224.0/216.182.239.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            213.199.160.0/213.199.191.255 

Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       192.168.1.215        212.48.8.140        
       0        0 DROP       tcp  --  *      *       192.168.1.215        212.48.8.140        
       0        0 DROP       udp  --  *      *       192.168.1.215        212.48.8.140        
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 137,138 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:7634 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:7634 
       0        0 DROP       all  --  *      *       0.0.0.0/0            111.221.64.0/111.221.127.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            213.199.160.0/213.199.191.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            157.52.0.0/157.60.255.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            65.52.0.0/65.55.255.255 
       0        0 DROP       all  --  *      *       0.0.0.0/0            2.192.0.0/2.195.255.255 




```

I've also edited my first post because it wasn't correct-as for the other question,this computer isn't also a router.

---

### Post by Doug S on 2012-10-26
Question: Are you testing new ufw rule sets (resulting in new iptables rules) without retsarting the computer? An established connection in the contrack table would be uneffected.
 
There is a "related established" route around what you want. However, and unless I missed something, I didn't see a path around for a new outgoing connection.
 
There are a bunch of rules in the ufw-user-input chain that are not needed, because there is no possible path via that rule. Example```
       0        0 DROP       all  --  *      *       0.0.0.0/0            207.46.0.0/207.46.255.255
```
 
I don't use ufw, so don't know if it is possible, but if you really want blanket blocking of those IP addresses, you might want to check them first in the INPUT and OUTPUT chains, before any RELATED,ESTABLISHED bypasses. That is what I do in my iptables rule set.

---

### Post by cogset on 2012-10-27
> **Doug S said:**
> Question: Are you testing new ufw rule sets (resulting in new iptables rules) without retsarting the computer? An established connection in the contrack table would be uneffected.

Well,I've observed that even after a reboot a connection from an IP range that should be blocked (according to a rule that has been successfully added before ) is established nonetheless-mostly so far I've seen this whilst using Skype (which,considering who is behind it,doesn't surprise me a great deal) but generally speaking I want to understand if specific programs can eventually override ufw user-set rules and how to prevent this.


> **Doug S said:**
> There is a "related established" route around what you want. However, and unless I missed something, I didn't see a path around for a new outgoing connection.
 
There are a bunch of rules in the ufw-user-input chain that are not needed, because there is no possible path via that rule. Example```
       0        0 DROP       all  --  *      *       0.0.0.0/0            207.46.0.0/207.46.255.255
```I don't use ufw, so don't know if it is possible, but if you really want blanket blocking of those IP addresses, you might want to check them first in the INPUT and OUTPUT chains, before any RELATED,ESTABLISHED bypasses. That is what I do in my iptables rule set.

I know that I've also thrown in some quite pointless rules whilst experimenting with ufw ;) ,however I would appreciate if the valid ones worked as I expected-which,if I got this one right,can't be really done in ufw and has to be done through iptables,which I find frankly kinda intimidating,to say the least.

---

### Post by Doug S on 2012-10-27
Could you say the specific address that is able to create the unwanted connection. I can not see the path in the OUTPUT chain for a NEW connection that would create the RELATED, ESTABLISHED by-pass on the INPUT chain. (I'm not saying it isn't there, just that I cann't see it).
 
Do you see the unwanted address in the UFW log file (perhps in /var/log/syslog)? look for "UFW AUDIT"

---

### Post by cogset on 2012-10-28
Ok ,keeping in mind that I only have a minimal understanding of what is going on here,here's a couple of established connections that I regularly find with the ss command each time I use Skype,and both should belong to the IP ranges that I've denied in UFW,as far as I can see.
So the question is,if these connections are actually needed by this program,and the UFW rules are valid,shouldn't I get an error message or something when using Skype,instead of having it work and the connections established bypassing the rules?
In other words,are the rules I've set in UFW actually valid,and if so,is what am I seeing  a  limitation  of UFW itself,meaning that to achieve what I'm after the use of iptables is mandatory?


ESTAB       0      0           192.168.1.xxx:32991    157.56.192.142:https                      
ESTAB       0      0           192.168.1.xxx:36280    78.141.179.16:12350

---

### Post by Doug S on 2012-10-29
Actually, I don't think the resulting iptables rules are correct for blocking a range.
I usually use a base IP address and a mask, i.e. 192.168.0.0/16.
When I saw what you were doing, I just assumed the syntax was correct for a range, but after testing something similar on my test computer, now I think the syntax is incorrect for a range. For a simple test, I ended up with these commands:```
sudo iptables -F OUTPUT
sudo iptables -A OUTPUT -s 0.0.0.0/0 -d 0.0.0.0/0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A OUTPUT -s 0.0.0.0/0 -m iprange --dst-range 192.168.111.100-192.168.111.200 -j LOG --log-prefix "ODROP:" --log-level info
sudo iptables -A OUTPUT -s 0.0.0.0/0 -m iprange --dst-range 192.168.111.100-192.168.111.200 -j DROP
sudo iptables -A OUTPUT -s 0.0.0.0/0 -d 0.0.0.0/0 -j LOG --log-prefix "OCATCH:" --log-level info
```And this result:```
Chain OUTPUT (policy ACCEPT 4 packets, 974 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     105    32380 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       2      120 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            destination IP range 192.168.111.100-192.168.111.200 LOG flags 0 level 6 prefix "ODROP:"
       2      120 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            destination IP range 192.168.111.100-192.168.111.200
       4      974 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "OCATCH:"
```

---

### Post by cogset on 2012-10-31
That explains why my rules are added in UFW but don't actually work,they are probably misinterpreted as valid addresses whilst they actually aren't.

---

### Post by cogset on 2012-11-12
After some more trying,I can definitely tell that even rules added to  UFW in the form of IP address + mask,like say 157.56.0.0/14,do not  prevent connections from this domain from being established when using  Skype:it's still unclear to me if IP blocking done via UFW is as  effective as using iptables and if programs are still under certain  circumstances allowed to eventually bypass these rules.

---

### Post by cogset on 2012-12-04
Well after some more experimenting with UFW,I've probably understood how to achieve that "blanket blocking" discussed here [http://ubuntuforums.org/showpost.php?p=12320078&postcount=7](http://ubuntuforums.org/showpost.php?p=12320078&postcount=7) ,as I've actually managed,as  proof of concept,to entirely prevent some sites from loading by using the simple syntax **ufw deny to [address]**  (this one in form of  IP address and a mask,like say 151.75.0.0/16),and the opposite **ufw deny out to [address]** .
This almost always work,except in some cases,where I cannot figure out why some of the usual suspects (read:connections to microsoft servers) won't be blocked when using Skype even when specifying the supposedly correct syntax.
Could it be that UFW does have some built-in limitations/overrides and that only iptables can really 100% control  what's going on ?

---

