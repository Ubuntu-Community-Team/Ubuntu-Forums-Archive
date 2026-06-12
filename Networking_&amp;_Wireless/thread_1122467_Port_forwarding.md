---
title: "Port forwarding"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by kondora on 2009-04-11
Hello,

The problem is as follows: I have three computers with external IPs: A - a1.a2.a3.a4, B - b1.b2.b3.b4, C - c1.c2.c3.c4. I want to forward port X on B machine in order to have the following scheme:

A tries to connect B (for example A: ssh -p X B), B forwards connection to C (if A tries to connect on port X then forward it to C on port X), so finally typing on A "ssh -p X B" we will get to C.

This I need for the software license forwading, I gave the ssh as an example.

Thank you very much in advance.

Gregory

---

### Post by Iowan on 2009-04-12
[Here]("https://help.ubuntu.com/community/IptablesHowTo") is a help page on IPTables (which includes info on port forwarding).  Hope it helps...

---

### Post by ktrnka on 2009-04-12
This is very simple to do via ssh. All you need to do is run this from computer A
```
ssh -L LocalPortNumber:c1.c2.c3.c4:RemotePortNumber user@b1.b2.b3.b4
```

That's all there is to it!

Then all connections from LocalPort will be sent to computer C to the remote port number. No other configuration is necessary.

---

