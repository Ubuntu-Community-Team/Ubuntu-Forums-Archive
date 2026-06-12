---
title: "iptables will not restore"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by MrStill on 2009-01-19
I thought I was having trouble with Firestarter and decided to configure my iptables manually. I used a guide which was suggested to me in this post: [http://ubuntuforums.org/showthread.php?t=1033952](http://ubuntuforums.org/showthread.php?t=1033952)

I found that when I run the iptables-restore command, the terminal just freezes. So, it seems, that providing network manager with a restore script does nothing. The result is that I have to run a shell script to refresh my iptables at every start up. I have tried having network manager run this script, adding this script to the login list in the sessions settings, and adding it to the start up list /etc/rc.local. I have also tried reinstalling iptables to see if that would make the restore command work properly. If more information is needed I am posting outputs from iptables -L and iptables-save. Any advise would be great.

Upon start up my iptables look like this:  

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  192.168.0.100        192.168.0.255       
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    all  --  anywhere             anywhere            
srcfilt    all  --  anywhere             anywhere            

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
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         all  --  anywhere             anywhere            

Chain f0to1 (3 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:6881:6889 state NEW 
logdrop    all  --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ssh state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:0:1023 dpt:ssh state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:6969 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:http-alt state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:https state NEW 
logdrop    all  --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
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
logdrop    all  --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      all  --  anywhere             localhost           
f0to1      all  --  anywhere             192.168.0.100       
f0to1      all  --  anywhere             192.168.0.255       
logdrop    all  --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      all  --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         all  --  anywhere             anywhere            

``` 

After I run a refresh script, my iptables look as they should

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6999 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:6881:6999 

```

iptables-save gives this report

```
# Generated by iptables-save v1.4.0 on Mon Jan 19 09:54:05 2009
*mangle
:PREROUTING ACCEPT [366:116960]
:INPUT ACCEPT [26:9080]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [127:10695]
:POSTROUTING ACCEPT [25:3246]
COMMIT
# Completed on Mon Jan 19 09:54:05 2009
# Generated by iptables-save v1.4.0 on Mon Jan 19 09:54:05 2009
*nat
:PREROUTING ACCEPT [349:108132]
:POSTROUTING ACCEPT [5:465]
:OUTPUT ACCEPT [78:5647]
COMMIT
# Completed on Mon Jan 19 09:54:05 2009
# Generated by iptables-save v1.4.0 on Mon Jan 19 09:54:05 2009
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 6881:6999 -j ACCEPT 
-A INPUT -j DROP 
-A OUTPUT -p tcp -m tcp --sport 6881:6999 -j ACCEPT 
COMMIT
# Completed on Mon Jan 19 09:54:05 2009
``` 

Thanks
Joseph

---

### Post by gettinoriginal on 2009-01-19
Hope this helps:  :P
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Ooops, sorry, did not check your link to see that the above link is already listed in there.

---

