---
title: "Samba/NFS Permissions"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-06-29
We are using Samba on our small network for an XP machine, but I would like to use NFS in Ubuntu.  We have that set up as well & it works good but files saved through NFS are locked when accessed from Samba.  Is there a way for me to relax the permissions so that this won't be an issue?  Actually I would like to relax the permissions in general.  The whole thing with copying a file to the server (vs. saving an open doc on the server) and having other people locked out is pretty annoying.  We just don't need that much security here.

---

### Post by nixscripter on 2010-06-29
Unfortunately, I don't know about the SAMBA side, but NFS usually is set up by making everything owned by one user, and then having every action done by every user be "as that user". This is user "squashing". Use the anonuid/anongid and all_squash options.

[http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)

Then maybe you can get SAMBA to do the same thing.

---

### Post by tracyandskye on 2010-07-01
Well this is what I had in my exports file:

```
/media/Data/server/Business/BPS 192.168.0.1/24(rw,no_root_squash,async)
```

Based on your link I tried this:

```
/media/Data/server/Business/BPS 192.168.0.1/24(rw,all_squash,anonuid=150,anongid=100,async)
```

The results are the same with either line.  XP can gain access to the files but they are read only.

---

### Post by tracyandskye on 2010-07-01
Well this is what I had in my exports file:

```
/media/Data/server/Business/BPS 192.168.0.1/24(rw,no_root_squash,async)
```

Based on your link I tried this:

```
/media/Data/server/Business/BPS 192.168.0.1/24(rw,all_squash,anonuid=150,anongid=100,async)
```

The results are the same with either line.  XP can gain access to the files but they are read only.

---

### Post by tracyandskye on 2010-07-01
Top?

---

### Post by tracyandskye on 2010-07-01
Top?

---

### Post by tracyandskye on 2010-07-01
This is weird.  When I replied it didn't move the post back up to the top.  Trying again.

---

### Post by nixscripter on 2010-07-02
I don't know SAMBA, so I don't knw how much help I can be, but I'll try.

That choice of UID and GID is one I assume can write the files?

You might want to make sure that user is also in an explicit write list:

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by tracyandskye on 2010-07-16
I don't know.  Anyone got anything?

---

### Post by tracyandskye on 2010-07-30
Bump

Still looking for an answer to this one.

---

