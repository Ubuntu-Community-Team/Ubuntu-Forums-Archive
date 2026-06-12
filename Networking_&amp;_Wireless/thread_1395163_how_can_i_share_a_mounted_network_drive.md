---
title: "how can i share a mounted network drive?"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by issax on 2010-01-31
Hi,

I'm looking for a solution, on how to share a network drive, for example:

I need my windows clients to be able to browse the content of a shared network drive that i have on the desktop of my ubuntu 9.10.

Is there any solution? because i'm using my ubuntu as a bridge between 2 separate network. this ubuntu has 2 network card, one configured to access the internal network and the other to access the outside network...
therefore the inside ethernet card is connected to the "smb" drive (i.e. smb://192.168.10.1/e$) which is the mounted drive on the desktop.
and i need the client from the outside network (i.e. 192.168.3.33) to browse the content of the mounted network drive...
please note that everything is well configured, i can easily browse any normal shared folder from anywhere on the ubuntu...

Your help is needed...

Thank you,

issax

---

### Post by johnson.d on 2010-02-02
Here you can use any one of the two options.

1)sharing using samba:

You can again share the folder on which the samba share has been mounted and use the login credentials of your bridge Ubuntu system.This will help you to share the folder in the internal network to the outside network.

2) Sharing using NFS:

Similarly You can also use NFS to share the mounted folder among the outside network.

---

### Post by superprash2003 on 2010-02-02
since its with windows machines , samba is a better option [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

