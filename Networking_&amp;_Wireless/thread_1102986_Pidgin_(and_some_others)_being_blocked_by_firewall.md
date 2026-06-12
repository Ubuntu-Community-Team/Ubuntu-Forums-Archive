---
title: "Pidgin (and some others) being blocked by firewall"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by shodan_uk on 2009-03-22
Hi all,

My firewall is blocking Pidgin and Football Manager Live (via Wine) even though I've configured it via Firestarter to allow traffic from everyone on the relevant ports: 443 for Pidgin, 9995/7 (and prob a few more) for FML.

The only way I can get these programs to connect is to disable the firewall via Firestarter.

Any ideas why this is?

Cheers,
Terry

p.s. I'm a relative Ubuntu n00b btw :)

---

### Post by shodan_uk on 2009-03-27
*bump*

Anyone?

---

### Post by shodan_uk on 2009-03-28
Anyone?

---

### Post by superprash2003 on 2009-03-28
in your terminal type **sudo iptables -L** and post output..

---

### Post by shodan_uk on 2009-03-28
Hi there,

Please see:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Please note, that's **without** the firewall active

Cheers,
Terry

---

### Post by shodan_uk on 2009-04-02
*bump*

---

### Post by superprash2003 on 2009-04-02
post an output with firewall active..

---

### Post by shodan_uk on 2009-04-02
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
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
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
LSI        icmp --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.6          192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.6          192.168.0.1         udp dpt:domain 
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
ACCEPT     all  --  192.168.0.7          anywhere            
ACCEPT     all  --  192.168.0.1          anywhere            
ACCEPT     all  --  192.168.0.4          anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:msnp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:msnp 
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp dpt:9997 
ACCEPT     udp  --  192.168.0.1          anywhere            udp dpt:9997 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9995 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9995 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (6 references)
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

### Post by superprash2003 on 2009-04-03
is 192.168.0.1 the ip of your machine?? do you have multiple interfaces?? post output of **ifconfig **from the terminal

---

### Post by shodan_uk on 2009-04-03
Hi again,

I believe 192.168.0.1 is the router.

Just the one interface.

ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d2:62:b6  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed2:62b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24511657 (24.5 MB)  TX bytes:3455681 (3.4 MB)
          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14036 (14.0 KB)  TX bytes:14036 (14.0 KB)

```

Cheers,
Terry

---

### Post by Bios Element on 2009-04-03
From a glance, Not being a firewall expect, I'd say you've mixed up your destination. The "Source" is from your router which is probably not correct. And the destination is "anywhere" when in reality it could be just 127.0.1 I may be mistaken but I think that's your problem.

EDIT: Also the other thing you should note is that Pidgin needs a port for each of the IM networks you connect too. Not just a single port for everything.

---

