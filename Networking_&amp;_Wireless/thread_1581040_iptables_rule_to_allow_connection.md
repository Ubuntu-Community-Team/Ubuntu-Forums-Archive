---
title: "iptables rule to allow connection"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by Choad on 2010-09-24
I have a laptop sharing its connection with a desktop. I would like the desktop to be able to connect to a mysql database on the laptop, but i keep getting connection refused.

I opened the port with iptables (or i thought i did) using the command

```
sudo iptables -I INPUT -p tcp --dport 3306 -j ACCEPT
```

which leaves me with these rules

```
richard@richard-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

but i still can't connect. using nmap from my desktop...

```
richard@richard-desktop:~$ nmap -p3306 192.168.1.65

Starting Nmap 5.00 ( http://nmap.org ) at 2010-09-24 14:03 BST
Interesting ports on ubuntu.lan (192.168.1.65):
PORT     STATE  SERVICE
3306/tcp closed mysql

Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds
richard@richard-desktop:~$ nmap -p3306 10.42.43.1

Starting Nmap 5.00 ( http://nmap.org ) at 2010-09-24 14:03 BST
Interesting ports on 10.42.43.1:
PORT     STATE  SERVICE
3306/tcp closed mysql

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds

```

does anyone know what is going wrong here?

---

### Post by gzarkadas on 2010-09-24
Your port is open; in fact:
-- all your input ports are open, since you have a default ACCEPT policy and no DROP rules
-- all your forward chain is open (due to rule #3), which *is* bad (unless your laptop is always in a protected network).

It is just that mysqld does not listen to the port you specify (3306). Possibly the documentation lags behind here.

To find where mysqld listens do a ```
sudo netstat -tap
``` and scan output to find a line ending in `/mysqld'. The number just before this is the port you are looking for.

Also it would be a good thing to change your iptables' default input and forward chain policies to DROP and remove forward rule #3.

---

