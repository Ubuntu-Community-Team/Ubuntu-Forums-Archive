---
title: "SSH problem"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by sreezon on 2012-02-19
I'm on Ubuntu 11.10 with gnome 3.0. The "ssh -x ..." doesn't work since I can't open new windows on my machine. If I do a regular "ssh ...", then I can open programs in the terminal only. How do I fix this bug? It used to work on the previous ubuntu.

---

### Post by kevdog on 2012-02-19
The server you are trying to connect to -- does it have x11forwarding enabled?  This must be specified in the sshd_config file.

---

### Post by roelforg on 2012-02-20
By default Xforwarding should be turned on,
I just ssh'd in to my home server (running ubuntu 11.10 server) and it just worked.
Note:
I did this (server hosts dns server, it's dns'd to server.local, i set up key-based auth, haven't touched sshd_config):
```

ssh -X server.local xclock

```
I appeared on my desktop just fine, note that the -X opt is case sensitive (you typed -x although it's usually safe to think you meant -X i've seen cases where is wasn't a typo and people were wondering why programs wont react to flags that are case-sensitive and spec'd with the wrong case, really!)

---

### Post by sreezon on 2012-02-20
OK, that worked. I was using -x instead of -X. Thanks for the help.

---

### Post by Perkins on 2012-02-21
For what it's worth, the lowercase x operator is what you would use when you wish to specifically *disable* X11 forwarding, if, for example, you were connecting to a server which had it enabled by default.

---

