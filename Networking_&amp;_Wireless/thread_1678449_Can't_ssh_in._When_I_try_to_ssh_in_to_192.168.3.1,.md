---
title: "Can't ssh in. When I try to ssh in to 192.168.3.1, I got a connection  timed out."
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by googling1000 on 2011-01-30
Hello,
I have got an Ubuntu Server 10.10 running.
For some reason, I just can't ssh in. I'm trying from inside the network first.
I have not had a chance to try from outside. I'd like to crack the problems one by one.


On this server, I have got a hotspot server (coova chilli) up and running. PC clients can get on the Internet fine. 
This server can ssh localhost, so I guess ssh is fine.
eth0 connects me to the router (WAN network)
eth1 connects to a switch (LAN network) 
From what I understand I should be able to ssh in to tun0. 
I added tun under /etc/modules

Right now, PC clients (that are connected to the switch) are assigned addresses of 192.168.3.xx automatically.
I can ping 192.168.3.1 from any PC clients with no problem.

Here is my ifconfig:
[http://www.fuengfu.com/ifconfig.JPG](http://www.fuengfu.com/ifconfig.JPG)

Here is the rules I have under /etc/chilli/up.sh. I'm a noob. I thought I have allowed ssh already.

```
# force-add the final rule necessary to fix routing tables
iptables -I POSTROUTING -t nat -o $HS_WANIF -j MASQUERADE

iptables -P INPUT DROP
iptables -I INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT


iptables -I INPUT -p icmp --icmp-type 8 -s 0/0 -d 192.168.3.1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -I OUTPUT -p icmp --icmp-type 0 -s 192.168.3.1 -d 0/0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#SSH Accept from tun0
iptables -I INPUT -i tun0 -p tcp -m tcp --dport 22222 --dst 192.168.3.1 -j ACCEPT

iptables -I INPUT -i eth0 -s 192.168.1.121 -p tcp -m tcp --dport 22222 --dst 192.168.1.122 -j ACCEPT

#SNMP
iptables -I INPUT -p udp -s 0/0 --sport 1024:65535 -d 192.168.3.1 --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I INPUT -p udp -i tun0 -d 192.168.3.1 --dport 161 -j ACCEPT

#iptables -t nat -I PREROUTING -i tun0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
#iptables -I INPUT -i tun0 -p tcp -m tcp --dport 3128 --syn -j ACCEPT
#iptables -t nat -I PREROUTING -p tcp -m tcp --dport 3128 -j DROP
#iptables -t nat -I PREROUTING -p tcp -m tcp --dport 8080 -j DROP
#iptables -t nat -I PREROUTING -p tcp -m tcp --dport 2121 -j DROP

iptables -t nat -I POSROUTING -o eth0 -j LOG
#squid Log
iptables -t nat -N logging
iptables -t nat -A PREROUTING -j logging

#iptables -t nat -A POSTROUTING -j logging
iptables -A INPUT -j LOG --log-level info --log-prefix "INPUT "
iptables -A OUTPUT -j LOG --log-level info --log-prefix "OUTPUT "
iptables -A FORWARD -j LOG --log-level info --log-prefix "FORWARD "
# HTTP:
iptables -t nat -A logging -p tcp --dport 80 -j LOG --log-prefix "HTTP: " \
--log-level info
# HTTPS:
iptables -t nat -A logging -p tcp --dport 443 -j LOG --log-prefix "HTTPS: " \
--log-level info
# SMTP:
iptables -t nat -A logging -p tcp --dport 25 -j LOG --log-prefix "SMTP: " \
--log-level info
# FTP:
iptables -t nat -A logging -p tcp --dport 21 -j LOG --log-prefix "FTP: " \
--log-level info
# IMAP:
iptables -t nat -A logging -p tcp --dport 143 -j LOG --log-prefix "IMAP: " \
--log-level info
# POP3:
iptables -t nat -A logging -p tcp --dport 110 -j LOG --log-prefix "POP3: " \
--log-level info
# MSN:
iptables -t nat -A logging -p tcp --dport 1863 -j LOG --log-prefix "MSN: " \
--log-level info
# JABBER:
iptables -t nat -A logging -p tcp --dport 5222 -j LOG --log-prefix "JABBER: " \
--log-level info

JABBERS
iptables -t nat -A logging -p tcp --dport 5223 -j LOG --log-prefix "JABBERS: " \
--log-level info
# ICQ/AIM
iptables -t nat -A logging -p tcp --dport 5190 -j LOG --log-prefix "ICQ/AIM: " \
--log-level info
# Yahoo
iptables -t nat -A logging -p tcp --dport 5050 -j LOG --log-prefix "YAHOO: " \
--log-level info
# IRC
iptables -t nat -A logging -p tcp --dport 6667 -j LOG --log-prefix "IRC: " \
--log-level info
# Gadu-Gadu
iptables -t nat -A logging -p tcp --dport 8074 -j LOG --log-prefix "GADU-GADU: " \
--log-level info

iptables -I INPUT -i lo -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 443 --syn -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 3990 --syn -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 4990 --syn -j ACCEPT

iptables -I INPUT -p tcp -m tcp --dport 80 --syn -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 53 --syn -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 67:68 --syn -j ACCEPT
iptables -I INPUT -p tcp -m tcp --dport 3306 --syn -j ACCEPT

iptables -A INPUT -i tun0 -j DROP
```


Please kindly advise.

Thank you in advance!

---

### Post by weedeater64 on 2011-01-30
192.168.1.3

maybe?

---

### Post by YesWeCan on 2011-01-30
ssh uses port 22 by default (this can be changed in /etc/ssh/sshd_config) so you need to allow port 22 in your firewall.

---

### Post by googling1000 on 2011-01-30
Hi YesWeCan,

It worked! Thank you so much for your time. That was real fast!!!

I'm just curious though. 
Yesterday, I took out the line that said
iptables -I INPUT -i tun0 -p tcp -m tcp --dport 22222 --dst 192.168.3.1 -j ACCEPT
and added this in place of it
iptables -A INPUT -p tcp -m tcp --dport 22 --syn -j ACCEPT

Why didn't it work? I thought that mean to allow 22 on any request coming in. Isn't it?

Thank you again ;)

You Rock!!!

---

### Post by regala on 2011-01-30
> **googling1000 said:**
> 
I'm just curious though. 
Yesterday, I took out the line that said
iptables -I INPUT -i tun0 -p tcp -m tcp --dport 22222 --dst 192.168.3.1 -j ACCEPT
and added this in place of it
iptables -A INPUT -p tcp -m tcp --dport 22 --syn -j ACCEPT

Why didn't it work? I thought that mean to allow 22 on any request coming in. Isn't it?

Thank you again ;)

You Rock!!!

hum, I guess it has something to do with the fact that 22222 is quite different from 22...

---

