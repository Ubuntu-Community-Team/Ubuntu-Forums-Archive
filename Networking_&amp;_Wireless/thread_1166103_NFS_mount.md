---
title: "NFS mount"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Ofloo on 2009-05-21
Every time I mount an NFS it works and after a few minutes it freezes the system why is that, or why could that be ?

I do mount -t nfs hostname:/directory/to/share /target/directory

works then after while it freezes on ls on df, ..

EDIT: using jaunty

---

### Post by Jose Catre-Vandis on 2009-05-21
Don't understand this bit?
> **Ofloo said:**
> after while it freezes on ls on df, ..

Try some of these:

1. Check you have **portmap** and **nfs-common** installed properly on your client

2. Try using the IP address instead of a name in your command

3. Try shortening the command by removing the "-t nfs", I never need it
```
sudo mount xx.xx.xx.xx:/files   /files
```

---

### Post by Ofloo on 2009-05-30
weird i haven't done anything that would suggest that it was fixed however it seems i was able to download a 1GB file over nfs without freezing it, ..

---

### Post by Jose Catre-Vandis on 2009-05-30
Was the problem just with big files or lots of small files? With file transfer or media streaming?

Good to hear it seems to have fixed itself though :)

---

### Post by Ofloo on 2009-11-11
going through different versions it still occours now and then, but not as often.

---

