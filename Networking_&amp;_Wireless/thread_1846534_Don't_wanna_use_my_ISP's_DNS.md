---
title: "Don't wanna use my ISP's DNS"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2011-09-19
Hi, I have recently purchased a 3G USB modem [http://airtel.in/3Gmobile/index.htm](http://airtel.in/3Gmobile/index.htm).

They have provided a tool which dials the connection, logs upload/download.

Strangely, Network Manager wont detect the modem

```

Bus 001 Device 006: ID 12d1:1436 Huawei Technologies Co., Ltd.
```My main issue is that I don't want to use my ISP's DNS(s). I have configured all possible connection in Network Manager to obtain the address only but /etc/resolv.conf showns 7-8 DNS servers. 

So, I created the file /etc/resolv.conf.head & mentioned 127.0.0.1 as the only nameserver coz I have already configured bind.

But despite creating  /etc/resolv.conf.head nslookup shows 


```
$ nslookup ubuntu.com
Server:        202.56.230.5
Address:    202.56.230.5#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156
```^ Instead of 127.0.0.1.


```
$ cat /etc/resolv.conf
nameserver 10.11.12.13
nameserver 10.11.12.14
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 202.56.230.5
nameserver 202.56.230.6
nameserver 127.0.0.1


```

```
$ cat /etc/resolv.conf.head 
nameserver 127.0.0.1
```





Please reply.

---

### Post by linuxyogi on 2011-09-19
There's no way ?

---

