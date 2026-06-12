---
title: "ICS Nightmare"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by musashi39 on 2009-02-10
I have an HP Pavilion a6244n Desktop, an Acer Aspire 3003LCi Laptop, a linksys WRT54G Wireless router, a verizion mobile broadband cell phone wireless usb thing (with vodaphone drives installed and all that working properly) and a Lexmark x7550 printer. The printer only works in windoze (burn in a bad place lexmark!) so I installed virtualbox.) When all this began I had to have my wired (eth0) connection unplugged (goes to the router) in order to get the internet through the verizon usb thing. So I'd have to disconnect the internet to print (which sucks!).

Then I figured out about ICS via firestarter and how that would solve all my problems........

The current state of things: 

My laptop wont connect wirelessly to the router. I have AES WPK2 or something like that enabled and changing this isn't such a great idea....(I've only had the wireless working in a hotel once about two months ago.)

I did manage to resurrect the USB internet (Which is the only internet that exists where I live).

No longer have access to the wired internet.

ICS worked once for about 15 minutes, with of course the laptop exception.

I don't know what files to post here. I tried finding a HOWTO and resetting all network configs w/o reinstalling ubuntu. And that's how I ended up here.

Thanks for reading this far!!!

:confused: Aaron :confused:

---

### Post by superprash2003 on 2009-02-10
well could you post output of sudo iptables -L .. i think your iptables must have been messed up.. you could flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html) and then use this tutorial to share your internet [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by musashi39 on 2009-02-10
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  14.sub-66-174-92.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-66-174-92.myvzw.com  anywhere            
ACCEPT     tcp  --  14.sub-69-78-96.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-69-78-96.myvzw.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             100.sub-75-209-250.myvzw.com 
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
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
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com udp dpt:domain 
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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
ACCEPT     all  --  192.168.0.0/24       anywhere            
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


I tried sudo iptables -flush or something like that a while ago.....

---

### Post by musashi39 on 2009-02-10
Also my eth0 network should be 192.168.11.XXX not sure if I need to add a route or something to bridge between 192.168.0.1....

---

### Post by musashi39 on 2009-02-10
I followed the tutorial for ICS and now my iptables are:

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  14.sub-66-174-92.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-66-174-92.myvzw.com  anywhere            
ACCEPT     tcp  --  14.sub-69-78-96.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-69-78-96.myvzw.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             100.sub-75-209-250.myvzw.com 
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
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
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com udp dpt:domain 
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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
ACCEPT     all  --  192.168.0.0/24       anywhere            
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

Nothing has changed.... :(

---

### Post by musashi39 on 2009-02-10
I think things are getting better. I think my only problem now is giving the router an IP address via DHCP I have my desktop pluged into the internet slot on the router. Is this right?


Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  14.sub-66-174-92.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-66-174-92.myvzw.com  anywhere            
ACCEPT     tcp  --  14.sub-69-78-96.myvzw.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  14.sub-69-78-96.myvzw.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.11.1        
INBOUND    all  --  anywhere             100.sub-75-209-250.myvzw.com 
INBOUND    all  --  anywhere             192.168.11.255      
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.11.0/24     state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.11.0/24     state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-66-174-92.myvzw.com udp dpt:domain 
ACCEPT     tcp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com tcp dpt:domain 
ACCEPT     udp  --  100.sub-75-209-250.myvzw.com  14.sub-69-78-96.myvzw.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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
ACCEPT     all  --  192.168.0.0/24       anywhere            
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

---

### Post by superprash2003 on 2009-02-11
well you cant give your router an ip via dhcp.. your router should have a static ip..

---

