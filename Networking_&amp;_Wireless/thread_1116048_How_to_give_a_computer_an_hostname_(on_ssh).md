---
title: "How to give a computer an hostname (on ssh)?"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by ofir_k on 2009-04-04
Hello,

I am running Ubuntu 8.04 with latest updates.

I have two machines which connects to a third one used as a file server, using ssh.

My router is configured with DHCP and hence sometimes changes the IP of the file server.

When that happens, I need to reconfigure the other two computers so they will be able to connect to the file server.

My question is: How can I give the file server a name, like a domain on the web, that will point to the file server no matter what IP address he has?

---

### Post by issih on 2009-04-04
There are other ways, involving wither enabling netbios broadcasts or setting up a wins or a dns server within the network, but probably the easiest thing to try first is to use the .local domain.

i.e. if your machine is called "malcolm", try connecting to "malcolm.local", this should try and do the name resolution by avahi (at least I think thats what it does).

So try this:

```
ping malcolm.local
```

with malcolm replaced by your machine's host name.

See if that works.

Hope that helps

---

### Post by ofir_k on 2009-04-04
WOW! Thanks!

That works fine for me.

---

### Post by issih on 2009-04-04
excellent :)

---

