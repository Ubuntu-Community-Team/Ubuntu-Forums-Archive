---
title: "Is it possible to connect to IRC session remotly in graphical session"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Mobidoy on 2010-11-19
I am always on the Ubuntu-qc irc room, well, almost always. The only time I disconnect is when I am on the road.

What I would like is to have my session open on my server and be able to connect to it from where I am.

I know I can install SIRC on the server and connect to it with Screen but, is there a way that i could connect to it with a irc program with a GUI like IRC ? 

Am I clear enough ?? lol

Thanx

---

### Post by chili555 on 2010-11-19
Can you ssh into the server from the road? If so, it's not necessary to have irc running on the server. Simply do:```
ssh -X -l user external.ip.of.server
```After you get logged in to the server, do:```
xchat
```

---

### Post by Mobidoy on 2010-11-19
> **chili555 said:**
> Can you ssh into the server from the road? If so, it's not necessary to have irc running on the server. Simply do:```
ssh -X -l user external.ip.of.server
```After you get logged in to the server, do:```
xchat
```

Yes I can ssh on it but, doing it that way means that all of what was said in the room while I was not connected is lost, or, sort of.

I want a way to be permanently logged and be able to connect to it and scroll back to see what i have missed ! 

I knew I was not clear enough lol... :)

---

