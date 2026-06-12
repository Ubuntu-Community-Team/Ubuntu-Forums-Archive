---
title: "Redirect rule with iptables"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by sl3ax on 2013-07-05
Hi to all. I need to create a rule with iptables that redirects all packets coming to 192.168.1.100 with destination port x to port y. So: ```
**192.168.1.100:x -> 192.168.1.100:y
```** This rule should work both with requests coming from external address and requests coming from an internal one. For example an IP of my LAN requests 192.168.1.100:x and the rule should do the work, and also: an external ip x.x.x.x (not in my LAN) requests myextip:x and the rule should also do the work correctly (assuming the NAT is configured). How could I do? Thanks in advance to all the forum. ):P

---

### Post by prodigy_ on 2013-07-05
```
iptables -t nat -A PREROUTING -p tcp -d 192.168.1.100 --dport x -j REDIRECT --to-port y
iptables -t nat -A PREROUTING -p udp -d 192.168.1.100 --dport x -j REDIRECT --to-port y
```

---

### Post by sl3ax on 2013-07-05
> **prodigy_ said:**
> ```
iptables -t nat -A PREROUTING -p tcp -d 192.168.1.100 --dport x -j REDIRECT --to-port y
iptables -t nat -A PREROUTING -p udp -d 192.168.1.100 --dport x -j REDIRECT --to-port y
```
Also I thinked to this. But the redirect doesn't work within a LAN. For example a local host make a requests for 192.168.1.100:x , and the redirect doesn't work. :(

---

### Post by prodigy_ on 2013-07-05
Sure it does. Example:

Server side:
```
#ss -ln
State      Recv-Q Send-Q                                             Local Address:Port                                               Peer Address:Port 
LISTEN     0      128                                                            *:22                                                            *:*    
# iptables -t nat -A PREROUTING -p tcp -d 192.168.137.4 --dport 12345 -j REDIRECT --to-port 22
```

Client side:
```
>telnet 192.168.137.4 12345
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
```

---

### Post by prodigy_ on 2013-07-05
[del]

---

### Post by sl3ax on 2013-07-05
> **prodigy_ said:**
> Sure it does. Example:

Server side:
```
#ss -ln
State      Recv-Q Send-Q                                             Local Address:Port                                               Peer Address:Port 
LISTEN     0      128                                                            *:22                                                            *:*    
# iptables -t nat -A PREROUTING -p tcp -d 192.168.137.4 --dport 12345 -j REDIRECT --to-port 22
```

Client side:
```
>telnet 192.168.137.4 12345
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
```

I tried too.
```

**#ss -ln**
tcp    LISTEN     0      128                    *:22                    *:*     
tcp    LISTEN     0      128                   :::22                   :::*     

``` ```
[B]#iptables -t nat -A PREROUTING -p tcp -d 192.168.1.100 --dport 12345 -j REDIRECT --to-port 22
[/B]
``` ```
**#iptables -t nat -L**
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             sl3ax.local  tcp dpt:12345 redir ports 22


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

``````
**#telnet 192.168.1.100 12345**
Trying 192.168.1.105...
telnet: Unable to connect to remote host: Connection refused

``````
**#ssh -p 12345 192.168.1.100**
ssh: connect to host 192.168.1.105 port 12345: Connection refused


```



I don't know if it could need, but my version of ip-tables is ***iptables v1.4.12 ***:(

---

### Post by prodigy_ on 2013-07-06
> **sl3ax said:**
> ```
#telnet 192.168.1.10**0** 12345
Trying 192.168.1.10**5**...
```
That's strange. I'm not entirely sure what could cause such behavior but packets are not being sent to the IP address you explicitly specify.

---

### Post by sl3ax on 2013-07-06
Excuse-me. That's because in my first post I write 192.168.1.100, but my internal IP was 192.168.1.105 and I tried to correct manually it.  So i tried all commands with 192.168.1.105 and after replaced "5" with "0" for continuity with the first post. But the rule doesn't work too.

---

### Post by prodigy_ on 2013-07-06
I see. If you have a firewall (other rules in iptables perhaps?) try disabling it and see if the redirect works.

---

### Post by sl3ax on 2013-07-06
It's the only rule in any table in iptables.

---

### Post by Doug S on 2013-07-06
I think we need some more details. Everything prodigy_ said should work. So, I wonder what is different between the two test setups, yours and prodigy_s? I will detail my test test setup, and maybe you can see the difference between mine and yours. I have a test computer at 192.168.111.140, that normally doesn't have any iptables rules at all, and does run sshd listening on port 22. I add the rule discussed herein:```
doug@test-smy:~$ sudo iptables -t nat -A PREROUTING -p tcp -d 192.168.111.140 --dport 12345 -j REDIRECT --to-port 22
```Now, I use another computer at 192.168.111.1 to check it, as per the previous examples in this thread:```
doug@doug-64:~$ telnet 192.168.111.140 12345
Trying 192.168.111.140...
Connected to 192.168.111.140.
Escape character is '^]'.
SSH-2.0-OpenSSH_6.1p1 Debian-4
x
Protocol mismatch.
Connection closed by foreign host.
doug@doug-64:~$
doug@doug-64:~$ ssh -p 12345 192.168.111.140
doug@192.168.111.140's password:
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-23-generic i686)
... [stuff deleted]...
Last login: Sat Jul  6 08:23:32 2013 from ns1.smythies.com
doug@test-smy:~$
```And I also check communications, on the above opened SSH session, via a tcpdump session on 192.168.111.140:```
doug@test-smy:~$ sudo tcpdump -n -nn -tttt -i eth0 port 12345
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-07-06 08:50:09.107395 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [P.], seq 3591404697:3591404745, ack 3028782444, win 314, options [nop,nop,TS val 238093961 ecr 450853], length 48
2013-07-06 08:50:09.107793 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [.], ack 48, win 1563, options [nop,nop,TS val 480966 ecr 238093961], length 0
2013-07-06 08:50:09.112035 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [P.], seq 1:49, ack 48, win 1563, options [nop,nop,TS val 480967 ecr 238093961], length 48
2013-07-06 08:50:09.112230 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [.], ack 49, win 314, options [nop,nop,TS val 238093962 ecr 480967], length 0
2013-07-06 08:50:09.113835 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [P.], seq 49:129, ack 48, win 1563, options [nop,nop,TS val 480967 ecr 238093962], length 80
2013-07-06 08:50:09.114042 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [.], ack 129, win 314, options [nop,nop,TS val 238093963 ecr 480967], length 0
2013-07-06 08:50:11.306256 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [P.], seq 48:96, ack 129, win 314, options [nop,nop,TS val 238094511 ecr 480967], length 48
2013-07-06 08:50:11.311054 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [P.], seq 129:209, ack 96, win 1563, options [nop,nop,TS val 481516 ecr 238094511], length 80
2013-07-06 08:50:11.311344 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [.], ack 209, win 314, options [nop,nop,TS val 238094512 ecr 481516], length 0
2013-07-06 08:50:12.200414 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [P.], seq 96:144, ack 209, win 314, options [nop,nop,TS val 238094734 ecr 481516], length 48
2013-07-06 08:50:12.201733 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [P.], seq 209:257, ack 144, win 1563, options [nop,nop,TS val 481739 ecr 238094734], length 48
2013-07-06 08:50:12.201897 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [.], ack 257, win 314, options [nop,nop,TS val 238094735 ecr 481739], length 0
2013-07-06 08:50:12.205840 IP 192.168.111.140.12345 > 192.168.111.1.39307: Flags [P.], seq 257:337, ack 144, win 1563, options [nop,nop,TS val 481740 ecr 238094735], length 80
2013-07-06 08:50:12.206068 IP 192.168.111.1.39307 > 192.168.111.140.12345: Flags [.], ack 337, win 314, options [nop,nop,TS val 238094736 ecr 481740], length 0
```

---

### Post by sl3ax on 2013-07-06
So,why my configuration doesn't work?

---

### Post by The Cog on 2013-07-06
If you're trying to redirect connections from your local box rather than redirecting connections that are routing through your box, then I think you should be adding the rules to the OUTPUT chain rather than the PREROUTING chain.

Lookee here at your Local process: [http://www.adminsehow.com/2011/09/iptables-packet-traverse-map/](http://www.adminsehow.com/2011/09/iptables-packet-traverse-map/)

---

### Post by sl3ax on 2013-07-06
> **The Cog said:**
> If you're trying to redirect connections from your local box rather than redirecting connections that are routing through your box, then I think you should be adding the rules to the OUTPUT chain rather than the PREROUTING chain.  Lookee here at your Local process: [http://www.adminsehow.com/2011/09/iptables-packet-traverse-map/](http://www.adminsehow.com/2011/09/iptables-packet-traverse-map/)  Thanks. I solved by using the OUTPUT chain of nat table. :-)

---

