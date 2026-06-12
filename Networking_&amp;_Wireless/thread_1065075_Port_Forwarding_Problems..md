---
title: "Port Forwarding Problems."
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by Godd on 2009-02-09
Hey.

I'm trying to forward two ports, 8000 and 8001. I have a Netgear router and I have the settings set up on it and I have my laptop set up with Static IP.

But I still don't have the ports open.

I don't think I have a firewall, I've turned it off on the router and I've never installed one on my comp. Does Hardy Heron have built in firewalls? I've configured Iptables but I'm not sure it's set up properly.

Help?

---

### Post by bicici on 2009-02-09
Hi,
Can you post the output of these commands, while your program is running :
```
sudo iptables -L -n
```
and the output of :
```
sudo netstat -ltunp
```

---

### Post by Godd on 2009-02-09
> sudo iptables -L -n
[sudo] password for godd: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

> 
sudo netstat -ltunp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      13576/sc_serv   
tcp        0      0 127.0.0.1:8001          0.0.0.0:*               LISTEN      13576/sc_serv   
tcp        0      0 192.168.1.6:53          0.0.0.0:*               LISTEN      16344/named     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      16344/named     
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN      6456/transmission
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5071/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      16344/named     
tcp6       0      0 :::5901                 :::*                    LISTEN      5859/vino-server
tcp6       0      0 :::53                   :::*                    LISTEN      16344/named     
tcp6       0      0 :::22                   :::*                    LISTEN      20454/sshd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      16344/named     
udp        0      0 192.168.1.6:53          0.0.0.0:*                           16344/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           16344/named     
udp        0      0 0.0.0.0:55372           0.0.0.0:*                           5032/avahi-daemon: 
udp        0      0 0.0.0.0:59612           0.0.0.0:*                           16344/named     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5032/avahi-daemon: 
udp        0      0 0.0.0.0:631             0.0.0.0:*                           5071/cupsd      
udp6       0      0 :::34567                :::*                                16344/named     
udp6       0      0 :::53                   :::*                                16344/named     


The Program is ./sc_serv. I see it there but I still don't have connectivity.

---

### Post by Godd on 2009-02-09
Correction. I have 8000 now open, I don't know how that happened. But I don't have connectivity on 8001.

---

### Post by bicici on 2009-02-09
According to iptables output, you do not have any firewall rule blocking (all rules have the policy ACCEPT).

According to netstat :
tcp 0 0 0.0.0.0:8000 0.0.0.0:* LISTEN 13576/sc_serv
tcp 0 0 127.0.0.1:8001 0.0.0.0:* LISTEN 13576/sc_serv

Your program listens on the network on port 8000/TCP (that's probably what you want).

But the program does not listen on the network on port 8001/TCP, it only listens on the loopback interface (127.0.0.1), so this port 8001/TCP cannot be reached from outside your computer, even if you manage to forward that port 8001 from your router to your computer.

Sorry I don't know the program sc_serv, so I cannot really help you on that.

Edit: There might be a (good) (security) reason why this program only listens on the loopback interface for port 8001/TCP.

---

