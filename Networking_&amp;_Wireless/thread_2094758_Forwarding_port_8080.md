---
title: "Forwarding port 8080"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by pulseplanet on 2012-12-14
Hello All
  I have a machine behind my main web server. I would like to redirect port 8080 to that machine. How do I do that?

Main server (eth0): 210.x.x.10
Machine behind main server (connected to eth1): 192.168.3.10

So if someone visits [http://210.x.x.10](http://210.x.x.10) they see may main server, but if they try [http://210.x.x.10:8080](http://210.x.x.10:8080) I would like then to go to the other machine (192.168.3.10). Thanks.

```

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  192.168.3.0/24       anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


```


Thanks,
M

---

### Post by Doug S on 2012-12-14
I think this command would add what you are looking for:```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.3.10:80
```However, I didn't think much for this reply. If it doesn't work properly for you, reply back and I'll think some more.

---

### Post by TheFu on 2012-12-14
I would do it at the router. That is much easier.

If you cannot, then you want a reverse-proxy.  Apache has a module for that, but pound, nginx, and ha-proxy can all work too.

I would not do it with iptables unless you ache to learn it.  Reverse proxies can do other things, like block ill-formed requests or requests trying to access protected resources or do things that iptables might do - connection and network tracking for hogs or DoS attempts.  The reverse proxies can also be a single front-end for SSL traffic, forwarding non-https traffic to the back-ends easily.

---

### Post by pulseplanet on 2012-12-14
Sorry, it did not work.


> **Doug S said:**
> I think this command would add what you are looking for:```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.3.10:80
```However, I didn't think much for this reply. If it doesn't work properly for you, reply back and I'll think some more.

---

### Post by Doug S on 2012-12-14
@TheFu: I was assuming the external facing server was also the router and that is where the iptables rule set is running.
 
@pulseplanet: Is your iptables rule set running on the 210.x.x.10 computer? If yes, I suspect a return path issue. It will take me awhile to test a solution. Could you give the output for```
sudo iptables -t nat -v -x -n -L
```

---

### Post by pulseplanet on 2012-12-14
```

~/bin> sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 15 packets, 1878 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080 to:192.168.3.10:8080

Chain INPUT (policy ACCEPT 15 packets, 1878 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 105 packets, 6434 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 50 packets, 2980 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      55     3454 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0 


```


My firewall script
```


#!/bin/bash

ifconfig eth1 192.168.1.1
ifconfig eth2 192.168.2.1
ifconfig eth3 192.168.3.1


# Flush all rules
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -o eth0 -i eth2 -s 192.168.2.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -o eth0 -i eth3 -s 192.168.3.0/24 -m conntrack --ctstate NEW -j ACCEPT


# Try redirecting port 8080 to port 80 on the PI 
sudo iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 8080 -j DNAT --to 192.168.3.10:8080
sudo iptables -A FORWARD -p tcp -d 192.168.3.10 --dport 8080 -j ACCEPT 


sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

sudo iptables-save > /etc/iptables.sav


```


> **Doug S said:**
> @TheFu: I was assuming the external facing server was also the router and that is where the iptables rule set is running.
 
@pulseplanet: Is your iptables rule set running on the 210.x.x.10 computer? If yes, I suspect a return path issue. It will take me awhile to test a solution. Could you give the output for```
sudo iptables -t nat -v -x -n -L
```

---

### Post by slickymaster on 2012-12-14
Take a look at this [tutorial]("http://www.hackorama.com/network/portfwd.shtml"). I think it might help you to achieve what you want.

---

### Post by pulseplanet on 2012-12-14
I have those lines in my script but still no luck.

Sorry for the repetition, but here is my script:

```

#!/bin/bash

ifconfig eth1 192.168.1.1
ifconfig eth2 192.168.2.1
ifconfig eth3 192.168.3.1


# Flush all rules
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -o eth0 -i eth2 -s 192.168.2.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -o eth0 -i eth3 -s 192.168.3.0/24 -m conntrack --ctstate NEW -j ACCEPT


# Try redirecting port 8080 to port 80 on the PI 
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d xxx.xxx.xxx.xxx --dport 8080 -j DNAT --to 192.168.3.10:80
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.3.10 --dport 80 -j ACCEPT


sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

sudo iptables-save > /etc/iptables.sav


```



On my main server, I can access the internal machine ([http://192.168.3.10](http://192.168.3.10)) and on my internal machine everything is open:


```
pi@raspberrypi ~ $ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```


> **slickymaster said:**
> Take a look at this [tutorial]("http://www.hackorama.com/network/portfwd.shtml"). I think it might help you to achieve what you want.

---

### Post by Doug S on 2012-12-14
With a default FORWARD policy of ACCEPT, you do not need this line:```
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.3.10 --dport 80 -j ACCEPT
```It is not clear to me what is wrong. Do you have forwarding enabled?```
cat /proc/sys/net/ipv4/ip_forward
```if it says 0 then you need to enable forwarding:```
sudo sysctl -w net.ipv4.ip_forward=1
```Edit: I re-arranged some computers and tested this on my system and it worked as expected.

---

### Post by pulseplanet on 2012-12-17
Doug,

[INDENT]```

~> cat /proc/sys/net/ipv4/ip_forward
1

``` [/INDENT] 

KB



> **Doug S said:**
> With a default FORWARD policy of ACCEPT, you do not need this line:```
sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.3.10 --dport 80 -j ACCEPT
```It is not clear to me what is wrong. Do you have forwarding enabled?```
cat /proc/sys/net/ipv4/ip_forward
```if it says 0 then you need to enable forwarding:```
sudo sysctl -w net.ipv4.ip_forward=1
```Edit: I re-arranged some computers and tested this on my system and it worked as expected.

---

### Post by Doug S on 2012-12-17
I notice that you have 3 network interfaces, and I wonder if return packets might be routing through the incorrect interface. Are you comfortable using a packet sniffer, such as tcpdump or wireshark? It might be time to look at actual packet flow to help figure out what is wrong. (Because I did something rather stupid, I had to resort to tcpdump when I tried to create your situation here.) The starting suggestion is to check for the packets being forwared:```
sudo tcpdump -n -nn -tttt -i eth3 host 192.168.3.10
```You should also see the return traffic.
Other differences between our two systems are that I do not use mangle and I use SNAT instead of MASQUERADE, but I don't think that should matter.

---

### Post by TheFu on 2012-12-17
> **Doug S said:**
> @TheFu: I was assuming the external facing server was also the router and that is where the iptables rule set is running.

A very valid assumption.  I'd assumed that since he had multiple machines on the same subnet, they were behind a router. 

Alas, it appears he really wants to use iptables. I'm an iptables "recipe" user, but I do most of those on a dedicated router that manages our public IP space.

All the other IP tables things I've needed were simple server firewalls - close everything except these 3 things or block completely as much from Russia, China and Ukraine as possible.  Sadly, we've had to block parts of France and the USA due to abuse too. Slowing down connections from abusive subnets didn't help enough.  

I can't imagine what we'd do if a real DoS attack happened.  Probably tell our clients to use a different DNS name (spares are good for that) and redirect the DoS target domain to 127.0.0.1?

Anyway, it looks to me like the forward into /proc might be the missing element, but I don't know.

---

### Post by pulseplanet on 2012-12-17
Doug,

   Still no luck (and I really appreciate your help).

tried to reach [http://localhost:8080](http://localhost:8080) while letting tcpdump execute.

```
~> sudo tcpdump -v -n -nn -tttt -i eth3 host 192.168.3.10
tcpdump: listening on eth3, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-12-17 11:12:09.895256 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.3.1 tell 192.168.3.10, length 46
2012-12-17 11:12:09.895271 ARP, Ethernet (len 6), IPv4 (len 4), Reply 192.168.3.1 is-at 00:04:23:d1:9f:f7, length 28
^C
2 packets captured
2 packets received by filter
0 packets dropped by kernel
```

KB



> **Doug S said:**
> I notice that you have 3 network interfaces, and I wonder if return packets might be routing through the incorrect interface. Are you comfortable using a packet sniffer, such as tcpdump or wireshark? It might be time to look at actual packet flow to help figure out what is wrong. (Because I did something rather stupid, I had to resort to tcpdump when I tried to create your situation here.) The starting suggestion is to check for the packets being forwared:```
sudo tcpdump -n -nn -tttt -i eth3 host 192.168.3.10
```You should also see the return traffic.
Other differences between our two systems are that I do not use mangle and I use SNAT instead of MASQUERADE, but I don't think that should matter.

---

### Post by Doug S on 2012-12-17
> tried to reach [http://localhost:8080](http://localhost:8080) while letting tcpdump execute.
No, that will not work. We only added a rule to, hopefully, deal with requests via eth0 to your external IP port 8080. You have to test it by coming from some computer on the WAN and trying to access [http://210.x.x.10:8080](http://210.x.x.10:8080) .

---

### Post by pulseplanet on 2012-12-17
Sorry, I did not mention that. 
I tried that ([http://210.x.x.x:8080)from](http://210.x.x.x:8080)from) a different computer as well. No luck.

(and ofcourse, I can access [http://210.x.x.x](http://210.x.x.x))



> **Doug S said:**
> No, that will not work. We only added a rule to, hopefully, deal with requests via eth0 to your external IP port 8080. You have to test it by coming from some computer on the WAN and trying to access [http://210.x.x.10:8080](http://210.x.x.10:8080) .

---

### Post by Doug S on 2012-12-17
Just as a sanity check, look for the incoming packets on eth0. Example (eth1 on my system):```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth1 port 8080
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-12-17 15:54:06.953674 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
2012-12-17 15:54:09.896454 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
2012-12-17 15:54:15.905349 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
```(Note: it doesn't get anywhere, because I removed the temporary forwarding rule on my system.)
Edit: By the way, your script (see post #6) is forwarding to port 8080 and not 80. It doesn't matter yet, as it seems the packets are not even leaving your main web server. Once, that is solved it will matter. You will have to set up apache2 on 192.168.3.10 to listen to port 8080 if that is what you want to do.

---

### Post by pulseplanet on 2012-12-18
```

sudo tcpdump -n -nn -tttt -i eth0 port 80 | head
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-12-18 10:04:59.619118 IP xx.xx.xx.xx.80 > xx.xx.xx.xx.43190: Flags [P.], seq 1484669878:1484670866, ack 622997235, win 65535, options [nop,nop,TS val 333720292 ecr 81209402], length 988
2012-12-18 10:04:59.619273 IP xx.xx.xx.xx.43190 > xx.xx.xx.xx.80: Flags [.], ack 988, win 47784, options [nop,nop,TS val 81209458 ecr 333720292], length 0
2012-12-18 10:04:59.620410 IP xx.xx.xx.xx.80 > xx.xx.xx.xx.43190: Flags [P.], seq 988:1943, ack 1, win 65535, options [nop,nop,TS val 333720292 ecr 81209402], length 955
2012-12-18 10:04:59.621252 IP xx.xx.xx.xx.80 > xx.xx.xx.xx.43190: Flags [P.], seq 1943:2857, ack 1, win 65535, options [nop,nop,TS val 333720293 ecr 81209402], length 914
2012-12-18 10:04:59.621271 IP xx.xx.xx.xx.43190 > xx.xx.xx.xx.80: Flags [.], ack 1943, win 47784, options [nop,nop,TS val 81209459 ecr 333720292], length 0
2012-12-18 10:04:59.621715 IP xx.xx.xx.xx.43190 > xx.xx.xx.xx.80: Flags [.], ack 2857, win 47784, options [nop,nop,TS val 81209459 ecr 333720293], length 0
2012-12-18 10:04:59.623041 IP xx.xx.xx.xx.80 > xx.xx.xx.xx.43190: Flags [P.], seq 2857:3719, ack 1, win 65535, options [nop,nop,TS val 333720293 ecr 81209402], length 862
2012-12-18 10:04:59.623198 IP xx.xx.xx.xx.43190 > xx.xx.xx.xx.80: Flags [.], ack 3719, win 47784, options [nop,nop,TS val 81209459 ecr 333720293], length 0
2012-12-18 10:04:59.625181 IP xx.xx.xx.xx.80 > xx.xx.xx.xx.43190: Flags [P.], seq 3719:6324, ack 1, win 65535, options [nop,nop,TS val 333720293 ecr 81209458], length 2605
2012-12-18 10:04:59.625354 IP xx.xx.xx.xx.43190 > xx.xx.xx.xx.80: Flags [.], ack 6324, win 47784, options [nop,nop,TS val 81209460 ecr 333720293], length 0
49 packets captured
50 packets received by filter
0 packets dropped by kernel

```


And: 


```

~>  sudo tcpdump -n -nn -tttt -i eth0 port 8080 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
**[NOTHING]**

```


```

~> sudo iptables -L
Chain INPUT (policy ACCEPT)
target * * prot opt source * * * * * * * destination * * * **




Chain FORWARD (policy ACCEPT)
target * * prot opt source * * * * * * * destination * * * **
ACCEPT * * all *-- *192.168.1.0/24 * * * anywhere * * * * * * ctstate NEW
ACCEPT * * all *-- *192.168.2.0/24 * * * anywhere * * * * * * ctstate NEW
ACCEPT * * all *-- *192.168.3.0/24 * * * anywhere * * * * * * ctstate NEW
ACCEPT * * tcp *-- *anywhere * * * * * * pi * * * * * * * * * tcp dpt:http
ACCEPT * * all *-- *anywhere * * * * * * anywhere * * * * * * ctstate RELATED,ESTABLISHED




Chain OUTPUT (policy ACCEPT)
target * * prot opt source * * * * * * * destination*

```



```

~> sudo iptables -nvL
Chain INPUT (policy ACCEPT 96M packets, 6668M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 9 packets, 468 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  eth1   eth0    192.168.1.0/24       0.0.0.0/0            ctstate NEW
    0     0 ACCEPT     all  --  eth2   eth0    192.168.2.0/24       0.0.0.0/0            ctstate NEW
 1286 97544 ACCEPT     all  --  eth3   eth0    192.168.3.0/24       0.0.0.0/0            ctstate NEW
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            192.168.3.10         tcp dpt:80
12544   13M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 112M packets, 920G bytes)
 pkts bytes target     prot opt in     out     source               destination


~> sudo netstat -tulnp | grep 8080
(nothing)


```




> **Doug S said:**
> Just as a sanity check, look for the incoming packets on eth0. Example (eth1 on my system):```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth1 port 8080
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-12-17 15:54:06.953674 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
2012-12-17 15:54:09.896454 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
2012-12-17 15:54:15.905349 IP 173.180.45.3.1551 > 173.180.45.4.8080: Flags [S], seq 2395425114, win 25200, options [mss 1460,nop,nop,sackOK], length 0
```(Note: it doesn't get anywhere, because I removed the temporary forwarding rule on my system.)
Edit: By the way, your script (see post #6) is forwarding to port 8080 and not 80. It doesn't matter yet, as it seems the packets are not even leaving your main web server. Once, that is solved it will matter. You will have to set up apache2 on 192.168.3.10 to listen to port 8080 if that is what you want to do.

---

### Post by Doug S on 2012-12-18
O.K. You will have to tell us more about your network, because, if I understand correctly, attempts to access access [http://210.x.x.10:8080](http://210.x.x.10:8080) do not even get to your main server. Obvioulsy, if the packets do not get to the main server in the first place, they can not be forwarded. Is there anything, other than perhaps a modem, between your main server and internet? Anything else you can tell us to help?

---

### Post by pulseplanet on 2012-12-18
Sorry for all the trouble, Doug. 
I really appreciate your taking the time to help me.

I found out what the trouble was.

```
sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d x.x.x.x --dport 8080 -j DNAT --to 192.168.3.10:80
```

I had the ip range wrong in the x.x.x.x above


> **Doug S said:**
> O.K. You will have to tell us more about your network, because, if I understand correctly, attempts to access access [http://210.x.x.10:8080](http://210.x.x.10:8080) do not even get to your main server. Obvioulsy, if the packets do not get to the main server in the first place, they can not be forwarded. Is there anything, other than perhaps a modem, between your main server and internet? Anything else you can tell us to help?

---

