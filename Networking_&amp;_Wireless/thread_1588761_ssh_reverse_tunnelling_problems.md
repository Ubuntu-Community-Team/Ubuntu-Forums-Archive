---
title: "ssh reverse tunnelling problems"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by aregjan on 2010-10-05
Hi.  I am learning how to do reverse ssh tunnelling, and sure enough I've made a mess of my ports and what not.

So I started by doing this:

```
ssh -nNT -R 1100:localhost:1100 myhomecomputer
```

Afterwards, when I tried to do 
```
ssh myhomecomputer -p 22

```
it for some crazy reason forwards me to port 22 on localhost.

If I understand the syntax correctly, it should have forwarded
*only* port myhomecomputer:1100 to port localhost:1100, and should have left port 22 alone.

Since doing this I ^C-ed the above ssh request, restarted sshd on
localhost, even rebooted localhost.  And yet, despite this, every time I try to ssh to myhomecomputer, using port 22, it sends me right back to
localhost.

So my question is -- how do I tell myhomecomputer remotely to stop forwarding?  And what's the right way in the future to reverse forward a specific port (say 1100)?

---

### Post by aregjan on 2010-10-05
I found out the problem...it is incredibly dumb.  It appears that as a result of my initial tunneling attempt our name server 
for some reason changed myhomecomputer's IP to 127.0.0.1.  Ports, ssh, and all that happy horseshit had **nothing **
to do with it.  The moment I replaced myhomecomputer with its actual IP it all worked as expected.

Stupid name server...

---

