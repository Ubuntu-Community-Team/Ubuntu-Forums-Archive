---
title: "Vinagre cannot connect"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by Vicker3000 on 2009-01-23
I would like to run a remote desktop of my desktop computer on my laptop.  I can get it to work the other way around just fine.  My laptop and desktop computers both have the same remote desktop preferences set.  Connecting to the desktop computer from the desktop computer works, as well as connecting to the laptop from the laptop, so the issue must have something to do with the networking between my computers and not vinagre.

When I try to connect to the desktop computer from my laptop, vinagre gives me a black screen where the desktop is supposed to appear.  After about 60 seconds, it pops up with an error message saying "Unable to connect".

What am I doing wrong here?  The desktop computer has a wired connection while the laptop is wireless, but I don't see why that should have any affect.  The desktop computer is running on Hardy and the laptop uses Intrepid.

---

### Post by superprash2003 on 2009-01-23
do you have firestarter or anything similar blocking it?? go to the terminal and type sudo iptables -L and post output

---

### Post by Vicker3000 on 2009-01-24
> **superprash2003 said:**
> do you have firestarter or anything similar blocking it?? go to the terminal and type sudo iptables -L and post output

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cns.beaverton.or.bverton.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.beaverton.or.bverton.comcast.net  anywhere            
ACCEPT     tcp  --  cns.cmc.co.denver.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.cmc.co.denver.comcast.net  anywhere            
ACCEPT     tcp  --  cns.saltlakecity.ut.utah.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cns.saltlakecity.ut.utah.comcast.net  anywhere            
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
ACCEPT     tcp  --  192.168.1.100        cns.beaverton.or.bverton.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.100        cns.beaverton.or.bverton.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.100        cns.cmc.co.denver.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.100        cns.cmc.co.denver.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.100        cns.saltlakecity.ut.utah.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.100        cns.saltlakecity.ut.utah.comcast.net udp dpt:domain 
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
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6112 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6112 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3724 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:3724 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6999 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6999 
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

---

### Post by teknorah on 2009-01-26
This was also happening to me.  I found that this can be caused by having the option: "Ask you for confirmation" checked in Remote Desktop Preferences on the machine you are trying to connect to.

This option, if checked, forces a popup on the machine you are trying to connect to with allow/deny buttons.  I think the reason for this being default on the Preferences is for security.  So that if you allowed remote desktop connections, it would only allow connect if the user on the machine you are connecting to is sitting there and clicks allow.

You should still setup a password and if you are only connecting when at home (in the other room), you could also add extra security to only allow local network connections on the advanced tab.

Hope this helps! :)

---

### Post by Vicker3000 on 2009-01-27
> **norahaura said:**
> This was also happening to me.  I found that this can be caused by having the option: "Ask you for confirmation" checked in Remote Desktop Preferences on the machine you are trying to connect to.

This option, if checked, forces a popup on the machine you are trying to connect to with allow/deny buttons.  I think the reason for this being default on the Preferences is for security.  So that if you allowed remote desktop connections, it would only allow connect if the user on the machine you are connecting to is sitting there and clicks allow.

You should still setup a password and if you are only connecting when at home (in the other room), you could also add extra security to only allow local network connections on the advanced tab.

Hope this helps! :)

This option is not checked.  Regardles, I _am_ sitting in front of the machine that I'm trying to connect to, so even if this was check I would be able to allow.  Thanks for the suggestion, though.

---

### Post by superprash2003 on 2009-02-06
have you made any custom changes to your iptables?? if not , you could try flushing your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

