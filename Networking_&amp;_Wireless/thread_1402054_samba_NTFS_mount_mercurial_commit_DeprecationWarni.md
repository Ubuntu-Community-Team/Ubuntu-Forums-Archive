---
title: "samba NTFS mount mercurial commit DeprecationWarning: use lock.release ..."
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by nasp on 2010-02-08
When trying to commit or get status from a mercurial repository on a mounted NTFS filesystem i get the following error:

```
/usr/lib/pymodules/python2.6/mercurial/lock.py:71: DeprecationWarning: use lock.release instead of del locklocker = self.testlock()
```

I found a couple of person who had the same problem but i can't find a solution.

Any ideas?

---

### Post by nasp on 2010-02-12
Anyone encountered the same issue?

---

### Post by nasp on 2010-04-26
Sorry for reviving this thread but I finally found a fix and since i had to dig in various bug report to do so I thought it might be worth it to share the solution.

This is my fstab entry. (using /etc/cifswf credentials)
```

//10.0.0.6/dev /home/simon/Reptile/www cifs exec,credentials=/etc/cifspw,umask=007,gid=46,uid=1000,quiet,file_mode=0666,dir_mode=0777 0 1

```

---

### Post by theindustry on 2011-02-07
> **nasp said:**
> Sorry for reviving this thread but I finally found a fix and since i had to dig in various bug report to do so I thought it might be worth it to share the solution.

This is my fstab entry. (using /etc/cifswf credentials)
```

//10.0.0.6/dev /home/simon/Reptile/www cifs exec,credentials=/etc/cifspw,umask=007,gid=46,uid=1000,quiet,file_mode=0666,dir_mode=0777 0 1

```

I just wanted to tell you that you're awesome. I've been trying to solve a similar issue and worked with it for over 10 hours before finding this thread which made Mercurial work instantly.

Kudos!

---

### Post by nasp on 2011-02-07
Cool! I'm happy it helped you, I knew it was worth posting :)

---

