---
title: "Can't ssh in from outside. Inside network is fine.H"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by googling1000 on 2011-02-04
Hello,

I have got a machine running on Ubuntu Server 10.10.

I can ssh from inside my house (thanks to a member here).

But, I just can't ssh from outside. I got the public ip of my router and went to a friend's to ssh in but to no avail.

Here is my iptables -L. 
root@hotspot:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:bootps:bootpc flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4990 flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3990 flags:FIN,SYN,RST,ACK/SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https flags:FIN,SYN,RST,ACK/SYN
ACCEPT     all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             hotspot             udp dpt:snmp
ACCEPT     udp  --  anywhere             hotspot             udp spts:1024:65535 dpt:domain state NEW,ESTABLISHED
[COLOR=Blue][B]ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             hotspot             tcp dpt:ssh[/B][/COLOR]
ACCEPT     icmp --  anywhere             hotspot             icmp echo-request state NEW,RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             hotspot
ACCEPT     udp  --  anywhere             hotspot             udp dpt:domain
ACCEPT     udp  --  anywhere             255.255.255.255     udp dpts:bootps:bootpc
ACCEPT     tcp  --  anywhere             hotspot             tcp dpt:4990
ACCEPT     tcp  --  anywhere             hotspot             tcp dpt:3990
DROP       all  --  anywhere             hotspot
DROP       all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `INPUT '
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `FORWARD '

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     icmp --  hotspot              anywhere            icmp echo-reply state RELATED,ESTABLISHED
LOG        all  --  anywhere             anywhere            LOG level info prefix `OUTPUT '
root@hotspot:~#


And, here is the rules I was told to add under /etc/chilli/up.sh. This machine is supposed to be an Internet hotspot running coovaChilli.

root@hotspot:~# vi /etc/chilli/up.sh

iptables -I POSTROUTING -t nat -o $HS_WANIF -j MASQUERADE

iptables -P INPUT DROP
iptables -I INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT


iptables -I INPUT -p icmp --icmp-type 8 -s 0/0 -d 192.168.3.1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -I OUTPUT -p icmp --icmp-type 0 -s 192.168.3.1 -d 0/0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#SSH Accept from tun0
[B][COLOR=Blue]iptables -I INPUT -i tun0 -p tcp -m tcp --dport 22 --dst 192.168.3.1 -j ACCEPT
iptables -I INPUT -p tcp --dport 22 -j ACCEPT[/COLOR][/B]

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

---

### Post by Sub101 on 2011-02-04
Have you set up your router to port forward?

---

### Post by gdonwallace on 2011-02-04
This is what I had to do for this to work.  As A side note, it works perfectly for me.

Take your laptop back to work with you first.  

1.  You will need to setup an IP address in your firewall and forward that new IP to the IP of the machine that you want to connect to.

2.  I'm sure You did this, but make sure that ssh is installed on both machines.

3.  SSH into the new IP address that was setup in step 1.  This will cause SSH to create a knew "key" for the known_hosts file.  

This will enable you to then connect to that machine through the new IP from anywhere.  

I do it from home all the time, I was over 100 miles away from work and was able to get connected. 

I also have a copy of the known_hosts file backed up through ubuntuone, that way if I have any problems, or have to reinstall ssh, that key is always there, just put it back into the ~/.ssh directory and you are good to go.

---

### Post by theozzlives on 2011-02-04
> **Sub101 said:**
> Have you set up your router to port forward?

The important thing is to make sure your port is forwarded in your router.

---

### Post by googling1000 on 2011-02-04
Man,

I feel so dumb.

You guys advise me to take a look at port forwarding. And,  that is when I remember my port forward page asked me for an IP address of the server and I had recently changed the IP since the old IP address was already used by an AP. Basically, what I did was to login to the router and updated the IP of the server.

Thank you all for your kindness :)

---

