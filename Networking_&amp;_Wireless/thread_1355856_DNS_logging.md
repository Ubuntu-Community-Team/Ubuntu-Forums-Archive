---
title: "DNS logging"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by chuina on 2009-12-15
Hi all,

I've installed DNS in my PC.
It can ping,host,dig.
Like:
```
root@desktop:~# host 192.168.1.10
10.1.168.192.in-addr.arpa domain name pointer ns.chuinample.com.

root@desktop:~# host ns.chuinample.com
ns.chuinample.com has address 192.168.1.10
```But can't log due to:

```
root@desktop:~# cat /etc/apparmor.d/usr.sbin.named | sudo apparmor_parser -r
apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
```Here is the permission of query.log:
```
root@desktop:~# ls -l /var/log/query.log 
-rw-r--r-- 1 bind root 1612 2009-12-16 00:21 /var/log/query.log
```My /etc/bind/named.conf.local files logging section is:


```

logging {
    channel query.log {
        file "/var/log/query.log";
        severity debug 3;
    };
    category queries { query.log; };
};

```What is the problem with logging ?

Thanks everyone!

---

### Post by chuina on 2009-12-16
Hey,
It start to log:P while i connect to the Internet.
Now it is logging fine.

But the Does Ubuntu Documentation tell anything about this ?
Thanks..

---

