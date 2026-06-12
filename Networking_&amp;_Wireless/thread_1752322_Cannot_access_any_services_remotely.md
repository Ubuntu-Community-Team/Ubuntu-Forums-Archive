---
title: "Cannot access any services remotely"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by brumb on 2011-05-07
Hi,

I've got a problem accessing any of the services running on my computer remotely. I have Apache, OpenSSH server, proftpd and Samba all running away, and up until now, providing sterling service.

Since yesterday I've not been able to access them from anything other than localhost.

[LIST]
[*]I can ssh into localhost OK, but cannot SSH by hostname or IP from another computer on the LAN.
[*]I can access the web pages served off the computer fine when I point firefox to localhost, but accessing the pages from another computer on the LAN (or outside) just times out.
[*]I can ftp files from the localhost to er... the localhost, but accessing it by IP or hostname doesn't work for other computers on the LAN.
[*]Samba shares are unavailable on the LAN, but can be accessed by pointing Nautilus to smb://localhost or smb://athos (where athos is the hostname)
[*]The same goes for VLC's http interface, and transmission-daemon's web interface.
[/LIST]
This is a significant problem for me. All of the useful things my computer used to do are broken.

The background to this is that I spilled tea all over my keyboard shortly before I noticed there was a problem. This may or may not have something to do with it. I forgot to unplug the keyboard before I began mopping up the spillage. Many random key presses brought me to the tty1 login console. (I have since found out that Ctrl-Alt F7 is the way back to the desktop from there, but the only thing I could think to do at the time was login and sudo reboot).

Is there a random key combo that has installed a firewall and blocked all incoming packets?

I don't know much about IPtables. Could someone take a look and see if there's a problem somewhere? If not, any other suggestions would be really helpful. I'm completely stumped on this one...:confused:


```
charlie@athos:~$ sudo iptables -L
[sudo] password for charlie: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  athos                anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  athos                anywhere            
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
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
ACCEPT     tcp  --  192.168.0.100        athos               tcp dpt:domain 
ACCEPT     udp  --  192.168.0.100        athos               udp dpt:domain 
ACCEPT     tcp  --  192.168.0.100        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.100        192.168.0.1         udp dpt:domain 
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

