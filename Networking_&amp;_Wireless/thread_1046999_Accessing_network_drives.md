---
title: "Accessing network drives"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by linuxmascot on 2009-01-22
Hello,

     I recently installed ubuntu 8.04 (hardy) ... my computer is connected to a LAN.

     I want to access the network drives from my ubuntu ... in windows I did the same typing in "RUN" the name of the network drive following \\

like \\spirit ... 

How can I access other computers similarly from ubuntu ... plzzz help!

---

### Post by x33a on 2009-01-22
go to places -> network. and if the drives are properly mounted, you'll be able to access them.

---

### Post by jvanbonn on 2009-01-22
I'm having the same difficulty.  My PLACES does not have a NETWORK option.  Do I need to install something?  I'm running Xubuntu 8.10.
Thanks!

---

### Post by x33a on 2009-01-22
@jvanbonn

maybe, this could be helpful

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

---

### Post by linuxmascot on 2009-01-22
am sorry, but I don't know how to mount network drives in linux ...

plzz ... someone can be of help?

thx people ...:)

---

### Post by linuxmascot on 2009-01-22
One more thing,

I went from Places -> Network

here I could see the different work groups but I couldn't view the files shared since they have username and password.

I don't know where to enter these so that I can view the files that I have access to ...

---

### Post by amac777 on 2009-01-23
> **linuxmascot said:**
> Hello,

     I recently installed ubuntu 8.04 (hardy) ... my computer is connected to a LAN.

     I want to access the network drives from my ubuntu ... in windows I did the same typing in "RUN" the name of the network drive following \\

like \\spirit ... 

How can I access other computers similarly from ubuntu ... plzzz help!

Try opening nautilus and then in the address bar type:

```
smb://spirit ...
```

---

