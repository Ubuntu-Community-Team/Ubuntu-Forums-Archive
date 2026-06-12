---
title: "SSH authenticity error"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by mpsrig on 2009-08-13
```
The authenticity of host 'optiplex-server.local (fe80::208:74ff:fea7:bd71%en1)' can't be established.
RSA key fingerprint is cf:08:50:1f:a8:fa:ee:cd:f1:69:19:b1:f5:ad:d6:5b.
Are you sure you want to continue connecting (yes/no)? no
Host key verification failed.

```

What does this mean?
This happens when connecting locally using the ```
ssh user@localhost
``` syntax.  Obviously, there's a security issue somewhere.  What is the problem?

---

### Post by chili555 on 2009-08-13
There is no problem. It means you haven't connected by SSH to this host before and so it hasn't yet stored an SSH key. Say yes, and it will do so and connect. This will happen the first time you SSH to any host. It's a way of asking if you are sure this is a safe place to go and are you sure you want to connect and receive all the viruses and malware within. Obviously, if you are connecting to localhost; that is, yourself, I hope you know it's safe. Hopefully, any host on your LAN is known by you to be safe, too. Connecting to [www.mysleazysite.ru](www.mysleazysite.ru) may be a bit more risky. Hence the warnings on first connect.

---

### Post by mpsrig on 2009-08-13
thanx alot
first time w/ ssh as u can tell

---

