---
title: "Some ports are closed by default?"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Arenim on 2010-11-01
Hi there!

When I scan my conputer locally, it shows a lot of opened ports:
```

doctor@dcstorage:~$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-01 19:20 MSK
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on dcstorage (127.0.0.1):
Not shown: 989 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql
5000/tcp open  upnp
5432/tcp open  postgresql
5544/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds


```But when I do the same from remote machine, the number of ports is much lesser:
```
doctor@doctor-desktop:~/lbd/set$ nmap 10.0.0.2

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-01 19:21 MSK
Interesting ports on 10.0.0.2:
Not shown: 995 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds

```iptables is clear:
```
doctor@dcstorage:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```/etc/hosts contains localhost and dcstorage words:
```
host.conf    hostname     hosts        hosts.allow  hosts.deny   
doctor@dcstorage:~$ cat /etc/hosts
#127.0.0.1      localhost
#127.0.1.1      dcstorage
127.0.0.1 dcstorage localhost rtpg-scgi.localhost rtpg

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```No firewall is used.

OS -- Ubuntu server 10.04 LTS

**Question**. How can I open other ports -- for postgresql for example?

---

### Post by Arenim on 2010-11-01
Oh, holy ****, i've forgot...

```
doctor@dcstorage:~$ netstat -l
&#1040;&#1082;&#1090;&#1080;&#1074;&#1085;&#1099;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1103; &#1089; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1086;&#1084; (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State      
tcp        0      0 dcstorage:5544          *:*                     LISTEN     
tcp        0      0 dcstorage:5000          *:*                     LISTEN     
tcp        0      0 dcstorage:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 dcstorage.local:domain  *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 dcstorage:ipp           *:*                     LISTEN     
tcp        0      0 dcstorage:postgresql    *:*                     LISTEN     
tcp        0      0 dcstorage:smtp          *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 *:6978                  *:*                     LISTEN     

```

Problem solved. Close the topic.

---

