---
title: "Problems with Firestarter and Samba"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by eyeteeth on 2010-01-18
I'm mainly trying to use a printer on an XP box.  I find whenever I have Firestarter running, it seems to disable all Samba networking.

I created the policies for Samba in Firestarter, and added a second policy for port 445 as I noticed when trying to print it was blocking that.  I don't get any messages now, but nothing will print, and I cannot "see" the network until I turn off Firestarter.

Here are the iptables from the system, the first set is will Firestarter disables, the second set with it turned on.  I need help making sense of it as to me it doesn't match my policy setting in the app.

------------------------------
**No Firestarter**

gcloon@ubuntu:~$ sudo iptables -L
[sudo] password for gcloon: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

-------------------------------------------------
[B]Firestarter on settings
Allow
Samba (SMB) 137-139 445     192.168.1.1/255.255.255.0
Microsoft-ds     445                  192.168.1.1/24[/B]


gcloon@ubuntu:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cns.westlandrdc.mi.michigan.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.westlandrdc.mi.michigan.comcast.net  anywhere            
ACCEPT     tcp  --  cns.area4.il.chicago.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.area4.il.chicago.comcast.net  anywhere            
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
ACCEPT     tcp  --  192.168.1.100        cns.westlandrdc.mi.michigan.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.100        cns.westlandrdc.mi.michigan.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.100        cns.area4.il.chicago.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.100        cns.area4.il.chicago.comcast.net udp dpt:domain 
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
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:microsoft-ds 
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
--------------------------
Seems a bit much for two policy settings.
Thanks

---

### Post by eyeteeth on 2010-01-18
Got it...  Seems to be an ongoing problem and I finally got the right search criteria.

Found the solution [HERE]("http://ubuntuforums.org/showthread.php?t=190542").[]("http://ubuntuforums.org/showthread.php?t=190542")

---

