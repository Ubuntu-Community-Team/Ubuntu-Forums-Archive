---
title: "can not connect network."
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by yescookie on 2009-02-26
Hi guys
I'm from China,my English is poor,but I really need your help.
This is my problem:
I use Ubuntu 8.10 64bit,and in a LAN.
Some days ago,the system can not connect network suddenly.
I have check the IP,DNS,GATEWAY,and they are all OK.
I try following commands:
1,ping [www.google.com](www.google.com)      //unknow host
2,nslookup [www.google.com](www.google.com)   //it replys google'IP
3,ping 203.208.39.99       //it works,and replys
4,I use firefox visit 203.208.39.99   //it works also

Maybe you will think the DNS is wrong,but I can connect the network in the Windows use same DNS.

---

### Post by Steve H on 2009-02-26
Have you put the address of your DNS into /etc/resolv.conf ??
You must follow this syntax: nameserver [ip address]

You could also try "System -> Administration -> Networking" if you don't like editing configuration files on your own.

---

### Post by yescookie on 2009-02-26
Hi,Steve H,thanks for your reply.
I have checked /etc/resolv.conf, the address of DNS is already putted on it.

---

### Post by Steve H on 2009-02-26
Has your LAN got a firewall?

---

### Post by yescookie on 2009-02-26
I'm not sure,I will ask the network managers in company.

---

