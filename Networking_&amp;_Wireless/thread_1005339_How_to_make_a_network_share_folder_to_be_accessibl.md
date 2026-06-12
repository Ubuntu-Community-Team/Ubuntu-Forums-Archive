---
title: "How to make a network share folder to be accessible for only some computers?"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by asaren on 2008-12-08
Hi All,

I'd like to make a network share folder on my computer to be accessible for only some computers in the network. How can i do this?

Thank you

---

### Post by theDaveTheRave on 2008-12-08
Asaren,

In my experience simply changing the netmask hides computers rather nicely!

You may also want to create a new group and have these terminals part of that group, give them each the same network mask, and they should then only be able to see each other.

they will still be accessible of course from elswhere by entering the //IPaddrss/sharedFolderName

but you will be able to limit access on this with a specific username and password.

Also with samba you can set it up to only accept hosts coming from IP's (I think).

David

---

### Post by superprash2003 on 2008-12-08
easy way out is username and password

---

