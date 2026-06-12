---
title: "ACL over NFS"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by jazzgossen on 2009-09-23
I've seen [this thread]("https://answers.launchpad.net/ubuntu/+question/18907") on Launchpad, saying that it's impossible to use ACL over NFS using a stock Ubuntu kernel. The reason is that the CIFS_XATTR attribute is not set, and it seems that Ubuntu doesn't want to set this attribute in the kernel. 

Anyway, if I compile a custom kernel with this attribute, does anyone know if it would be enough to do it on one machine, and in that case should it be the NFS server or client, or would it have to be enabled on all computers?

---

### Post by randyklein99 on 2010-03-18
Wanting to know if you ever found an answer...

---

### Post by jazzgossen on 2010-03-29
Not yet, but I'll try setting it up again in a month or so. I'll post back when I know something.

---

### Post by randyklein99 on 2010-05-29
Anything new with 10.04?

---

### Post by jazzgossen on 2010-05-31
I haven't tried it yet, but I know I have read (although I don't remember where now) that Ubuntu now does support ACL over NFS. So it should work fine with 10.04 (and I think also 9.10).

---

