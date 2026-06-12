---
title: "cachefilesd --- operation not supported"
date: 2013-07-06
forum: Networking &amp; Wireless
---

### Post by iaw4 on 2013-07-06
I have two ubuntu 13.04 machines---well, cinnamon mint olivia. both computers are SSD-based.   one runs an NFS server, the other is the NFS client.  NFS works fine.  now I wanted to add the cachesfiled daemon to speed it up.

**on the server**, the exported directory is on a partition that is

```
UUID=blah /home           ext4    defaults,noatime,user_xattr        0       2
``` 

and after a remount,"[FONT=Courier New]setfattr -n user.name -v val ~/.bashrc[/FONT]"  does not give me an error.


**on the client**, the /etc/cachesfiled.conf is

```

dir /var/cache/fscache
tag mycache
brun 10%
bcull 7%
bstop 3%
frun 10%
fcull 7%
fstop 3%

```

and its fstab for the nfs-imported directory is like
```

server:/home/somewhere/somedir  /home/somewhere/somedir nfs rw,fsc,hard,intr 0 0

```

Although nfs works, when I try to start the cachefilesd, either before or after I mount the nfs volume, it always fails.  on my attempt to [FONT=Courier New]/etc/init.d/cachefilesd start[/FONT], the syslog tells me 

```

Jul  5 21:15:30 client cachefilesd[27530]: About to bind cache
Jul  5 21:15:30 client cachefilesd[27530]: CacheFiles bind failed: errno 95 (Operation not supported)
```

I wish I could elicit more clarification to backtrack where it fails, but I don't know how.  I tried to start the cachefilesd daemon by hand with a few "-d".  nothing more descriptive.

obvious problem?

sincerely,

/iaw

---

### Post by skyglow on 2013-09-22
did you solve?
i don't have caching at all, although i've no errors.

---

