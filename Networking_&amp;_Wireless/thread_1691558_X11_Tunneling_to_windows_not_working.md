---
title: "X11 Tunneling to windows not working"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by DexterLB on 2011-02-20
I want to tunnel X apps to windows with PuTTY. I have the following in my sshd_config:
```

X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AllowTcpForwarding yes
UseLogin no

```
Putty successfully enables X forwarding and $DISPLAY is ```
localhost:10.0
``` in the putty session. However when I try to run something like xeyes I get: ```
Error: Can't open display: localhost:10.0
```
any ideas?

---

### Post by Miguel Tavares on 2011-02-20
hi,
try to get the most of the logs so within your home folder or for the user that your connecting there should be a .xsession* log. check it out for more debuging.
also output from "echo $DISPLAY" would be great.

Kindest Regards

Miguel Tavares

---

### Post by DexterLB on 2011-02-20
Sorry it turned out XMing wasn't running :D I started it properly and everything is ok now

---

### Post by Miguel Tavares on 2011-02-20
Cool, so SOLVE this thread please --> [Thread Tools]("http://ubuntuforums.org/showthread.php?p=10475940&nojs=1#goto_threadtools")

---

### Post by DexterLB on 2011-02-20
Thanks for reminding me. :)

---

