---
title: "Msn Messenger from Schools closed enviroment"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by boubbin on 2010-02-12
Hey guys,

This is not Ubuntu-specific thing-y per se but i will go on.
I cant connect to msn messenger service from my university's environment cause the administration has blocked all the ports that messenger needs.

I have a server in my home which runs Ubuntu and i would like to create a tunnel from my school to this server, and connect to messenger service through that tunnel, i have been trying to get this working with ssh, and i successfully made it in a test environment in my home, but the same thing wont work from school.

Here is the code
```
ssh -NL 1863:messenger.hotmail.com:1863 my.ssh.server.fi -l boubbin -v
```

Output
```
debug1: Connection to port 1863 forwarding to messenger.hotmail.com port 1863 requested.
debug1: channel 1: new [direct-tcpip]
channel 1: open failed: connect failed: Connection timed out
```

---

### Post by Elfy on 2010-02-12
If the university has a policy blocking messenger then talk to them about it.

Thread closed.

---

