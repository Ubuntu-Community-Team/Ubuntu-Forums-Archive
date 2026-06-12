---
title: "ftp: ubuntu wont connect, but Windows and Mac os will"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by zpon on 2009-04-25
This problem seems stranger and stranger, with earlier versions of ubuntu this have been able to connect just fine, but since some were in the early betas of 9.04 I sopped being able to connect to three of the ftp servers I work with on daily basis, this is kind of a problem. 
On all other computers (Mac and Windows) in the house I am able to connect just fine even my router can telnet to server, I also have access to a couple of debian computers, which is also able to connect without problems.

When I try telnet to port 21 from my computer all I get is
```
$ telnet ftp.frise.dk 21
Trying 80.82.99.228...
Connected to ftp.frise.dk.
Escape character is '^]'.
```

where as I should receive something like 
```
$ telnet ftp.frise.dk 21
220 ProFTPD 1.3.1rc2 Server (DHT www2.dht.dk) [80.82.99.228]
```

I haven't experienced any other ftp servers I could not connect to, only the three mentioned before.

I thought about filling in a bug on this, but I thought I would give it a try here first. Any help is appreciated.

---

### Post by drhiii on 2009-04-28
I am having the exact same problem with telnet.  Unable to connect out to port 25.  What are we missing?  Have some filters been applied in 9.04 that block certain ports?

---

### Post by zpon on 2009-04-30
> **drhiii said:**
> I am having the exact same problem with telnet.  Unable to connect out to port 25.  What are we missing?  Have some filters been applied in 9.04 that block certain ports?

I am thinking the same. I think I am going to file a bug report on the issue.

---

### Post by zpon on 2009-06-08
I have created a bug for this problem [https://bugs.launchpad.net/ubuntu/+source/netkit-ftp/+bug/377609](https://bugs.launchpad.net/ubuntu/+source/netkit-ftp/+bug/377609)

---

