---
title: "need to unlimit trafic on tcp ip port"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by sajil2 on 2013-07-31
hi
i am using ubuntu 12.04 lts.i have traffic coming in on port 17000.but its only allowing 1000 clients.then its getting congested.i ran netstat -a . i am seeing lot of
TIME_WAIT.how do i unlimited traffic to that port please

---

### Post by zero2xiii on 2013-07-31
Hay,

What service is using port 17000 on your system that is being accessed by MORE than 1000 connections?

Cheers

---

### Post by sajil2 on 2013-08-08
i get error
TCP: Possible SYN flooding on port 17000. Sending cookies.  Check SNMP counters.

---

### Post by SeijiSensei on 2013-08-08
SYN floods are a form of denial-of-service attack.  Are you expecting 1000 simultaneous clients?  What are you running on port 17000?

Try adding this iptables rules to log the origins of the incoming packets:

```
/sbin/iptables -I INPUT -p tcp --dport 17000 -j LOG
```

Using "-I" puts this rule at the top of the list.  The offending packets will be logged in /var/log/kern.log or /var/log/syslog depending on how syslog is configured.

---

