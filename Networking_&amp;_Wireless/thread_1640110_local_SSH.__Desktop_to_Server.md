---
title: "local SSH.  Desktop to Server"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by jus71n742 on 2010-12-07
I am playing around with 5 machines total.  I have a laptop running desktop 10.04
4 desktops running 10.04 server.

I can't plug these into the network, but the laptop can get wireless.  
I have installed server on only one desktop thus far.  the wireless connection is shared from the laptop and is working.  I have all 5 linked together with a dumb switch.

I was trying to SSH into the server and I cannot, however, I CAN ssh from the server to the laptop using just IP's  But not vice versa.

```

clusternode@t42:$ ssh node3@x.x.x.x
node3@x.x.x.x's password:
Permission denied, please try againclusternode@t42:$ ssh node3@x.x.x.x
node3@x.x.x.x's password:
Permission denied, please try againclusternode@t42:$ ssh node3@x.x.x.x
node3@x.x.x.x's password:
Permission denied, (publickey, password)

```

so what am I doing incorrectly to cause this error?
I have also tried 
```

ssh node3@localhost

```
same results

---

### Post by surfer on 2010-12-07
is node3 really your username? if your username on the server is the same as on the client you can just
```
$ ssh x.x.x.x

```
otherwise enter the username you have on the server
```
$ ssh user@x.x.x.x

```

---

### Post by jus71n742 on 2010-12-07
Yes I have the username node3, no I am using a username of t42 on the laptop.  what you see is exactly what I put in.  minus the x.x.x.x of course.

---

### Post by jus71n742 on 2010-12-10
Problem Solved, I manually hooked up a monitor and keyboard to the systems and wrote down their ip's and then tried.  I have the last number wrong.

---

### Post by amauk on 2010-12-10
you can use nmap to scan your subnet and return the address of all machines

Eg. to ping all machines from 192.168.1.1 - 192.168.1.254, do:
```
nmap -sP 192.168.1.0/24
```

The /24 means match the first 24 bits only (3 sets of 8 bits), wildcard the rest

---

