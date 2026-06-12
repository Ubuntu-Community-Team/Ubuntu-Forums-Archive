---
title: "ftp errors?"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-01-20
my web hosting service (luckyregister/secureserver) has been uncharacteristically distant and unhelpful with this, so i'm turning to the ubuntu-ers for help!

in short, whenever i mount my ftp folder in nautilus or open a connection in filezilla, i receive an error of > Error: Connection closed by server
in filezilla, choosing keep-alive doesn't change anything. it's rather annoying when i'm working on something and the connection suddenly closes. any ideas where i can start trouble-shooting this?

---

### Post by jonobr on 2009-01-20
Hello


Try running in command line and see what happens.

Open a terminal window,

type 
ftp yourserver.com

enter your username and password.

Do normal ftp stuff like 

ls

try grabbing some files using mget *

I recall one version had a bug in nautilus for FTP , however, I dont think thats your case here, as it gives ftp error from the server.

If this shows the same, I think you may need to do a wireshark trace.
That way it can give you some evidence to your providor for whats wrong

---

### Post by moore.bryan on 2009-01-20
interesting... i get this:
```
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 9 of 50 allowed.
220-Local time is now 12:52. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 3 minutes of inactivity.

```

so, can i assume it's a "timeout" issue with my host?

---

### Post by jonobr on 2009-01-20
Mmmmm.... IM not sure If or how Nautilus can keep that session alive.
I did a few googles but couldnt find anything.

3 minutes seems very very short.

---

### Post by moore.bryan on 2009-01-20
three is really irritating... i've been able to extend the time-out in filezilla by issuing keep-alive commands, which i shouldn't have to do, but i'm looking for the same keep-alive functionality on nautilus. i even tooled-around the nautilus scripts page, but without luck.

i do recall in my web travels, coming across a bug in launchpad about nautilus not having the ability to keep-alive.

---

