---
title: "manually manipulating iptables ..."
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-03-22
Hi all,

I am trying to learn a bit about iptables

below I have some rules.

What i am tryiny to accomplish on the machine in question is to open ports
tcp: 20,21,22,25,53,80,110,143,443,3306,8080,10000,135,139,445
udp: 53,3306,5353,137,138
on the machine in question.  Furthermore i only want these ports accessible to my LAN located at 192.168.1.0/24.

Are these rules below correct for this scenario?

Also if i wanted to open a port full to the world do I just drop the -s 192.168.1.0/24 or do i replace it with -s 0.0.0.0/0.

Thank you.

```

#UNKNOWN
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 20 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 20 --syn -j REJECT

#WEBMIN
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 10000 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 10000 --syn -j REJECT

#FTP
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 21 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 21 --syn -j REJECT

#SSH
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 22 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 22 --syn -j REJECT

#SSL
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 443 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 443 --syn -j REJECT

#MYSQL
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 3306 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 3306 --syn -j REJECT
/sbin/iptables -I INPUT -p udp -m udp -s 192.168.1.0/24 --dport 3306 --syn -j ACCEPT
/sbin/iptables -I INPUT -p udp -m udp --dport 3306 --syn -j REJECT

#DNS
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 53 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 53 --syn -j REJECT
/sbin/iptables -I INPUT -p udp -m udp -s 192.168.1.0/24 --dport 53 --syn -j ACCEPT
/sbin/iptables -I INPUT -p udp -m udp --dport 53 --syn -j REJECT
/sbin/iptables -I INPUT -p udp -m udp -s 192.168.1.0/24 --dport 5353 --syn -j ACCEPT
/sbin/iptables -I INPUT -p udp -m udp --dport 5353 --syn -j REJECT

#WEB
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 80 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 80 --syn -j REJECT
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 8080 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 8080 --syn -j REJECT

#MAIL
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 25 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 25 --syn -j REJECT
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 110 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 110 --syn -j REJECT
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 143 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 143 --syn -j REJECT

#SAMBA
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 135 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 135 --syn -j REJECT
/sbin/iptables -I INPUT -p udp -m udp -s 192.168.1.0/24 --dport 137 --syn -j ACCEPT
/sbin/iptables -I INPUT -p udp -m udp --dport 137 --syn -j REJECT
/sbin/iptables -I INPUT -p udp -m udp -s 192.168.1.0/24 --dport 138 --syn -j ACCEPT
/sbin/iptables -I INPUT -p udp -m udp --dport 138 --syn -j REJECT
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 139 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 139 --syn -j REJECT
/sbin/iptables -I INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 445 --syn -j ACCEPT
/sbin/iptables -I INPUT -p tcp -m tcp --dport 445 --syn -j REJECT

```

---

