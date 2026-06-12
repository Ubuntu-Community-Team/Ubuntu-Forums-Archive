---
title: "howto and message passing over the network"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by hardfire_avk on 2010-06-25
Hello,
this is what i actually need.
We have a ubuntu machine on the network with number of users in it.
Basically, when other users connect via telnet i want then to get particular messages depending on the user . The message will be set by the administrator or a particular user with privs.

Similarly we also need a to-do app via which users can update their work and see each others progress .
Its all in a local network.
Do tell what would be the best way to do it!

---

### Post by okplayer02 on 2010-06-25
well i know you were asking about something specific for telnet but these 2 commands allows you to send messages to users on the machine, via the command line. 

```
man wall
```
```
man write
```



Hello,
this is what i actually need.
We have a ubuntu machine on the network with number of users in it.
Basically, when other users connect via telnet i want then to get particular messages depending on the user . The message will be set by the administrator or a particular user with privs.

Similarly we also need a to-do app via which users can update their work and see each others progress .
Its all in a local network.
Do tell what would be the best way to do it![/QUOTE]

---

### Post by VH-BIL on 2010-06-25
Example:
```
echo "Message To Send" | write user@host pts/0
```

---

