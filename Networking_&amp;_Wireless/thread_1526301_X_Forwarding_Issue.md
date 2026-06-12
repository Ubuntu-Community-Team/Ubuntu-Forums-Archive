---
title: "X Forwarding Issue"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by quattro_cs on 2010-07-07
Hey everyone.

I've been trying to get XForwarding to work to my home machine from a school server to no avail. I've been able to get XForwarding to work to my laptop that has cygwin installed, so the I know the server is configured correctly.

I've been trying to connect with both

```

ssh -XC myusername@myschoolserver
ssh -YC myusername@myschoolserver

```

and I just see the error message Xt error: Can't open display when I run any graphical application, such as 

```
xterm&
```

The output of my local DISPLAY is 

```
homebase:0.0
```

and the output on myschoolserver is

```
myipaddress:0.0
```

I've ran ```
ps -ef | grep X
``` and seen the nolisten command both locally and on the server.

I have 127.0.0.1 localhost at the top of my local /etc/hosts file as well as edited the local /etc/ssh/sshd_config to allow for X Forwarding.

I am at a complete loss as this is extremely annoying. I am working with code on the server that requires me to run a graphical component to test it. Any ideas?

---

### Post by quattro_cs on 2010-07-09
bump?

---

