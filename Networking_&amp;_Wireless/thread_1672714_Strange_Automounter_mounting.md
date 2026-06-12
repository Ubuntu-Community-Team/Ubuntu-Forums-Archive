---
title: "Strange Automounter mounting"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by SchenkeM on 2011-01-21
Hi all,

I want to import some data from a NFS-server, but there is some thing strange.
If I go to the imported directory "/imported", I don't see its content. If I "cd /Imported" and type something in terminal, for instance "test", it creates a directory "/imported/test". If I now "cd /imported/test" and type "ls" in that directory, I get the content that I actually wanted to have in "/imported". Has anyone experienced such a strange thing already? Or is there something in my configuration?

This is want I get by typing "exportfs" on the server
```

...
/exportdir xxx.xx.xx.0/255.255.255.0
...

```Looks fine to me.

This is my /etc/auto.master:
```

...
+auto.master
/imported    /etc/auto.imported

```This is my /etc/auto.imported:
```

* -rw,hard,intr,tcp,wsize=8192,rsize=8192 <NFS-SERVER>:/exportdir

```

---

