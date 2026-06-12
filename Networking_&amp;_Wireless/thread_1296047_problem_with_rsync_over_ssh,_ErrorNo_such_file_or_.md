---
title: "problem with rsync over ssh, Error:No such file or directory (2)"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by rodmena on 2009-10-20
Hi everybody. this is my first post here.:)
I use this code to sync my two ubuntu 9.04 machines:

```
rsync -av 192.168.0.1:/home/farsheed/projects/BurnCity/ /home/farsheed/Public
```

After entering the remote machine password, I got this error:

```
receiving incremental file list
rsync: change_dir "/home/farsheed/projects/BurnCity" failed: No such file or directory (2)

sent 8 bytes  received 10 bytes  0.88 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1524) [receiver=3.0.5]

```

Could anyone help me to solve my problem. I know the directory exists.
Thanks in advanced.

---

### Post by uncle-c on 2009-10-20
> **rodmena said:**
> Hi everybody. this is my first post here.:)
I use this code to sync my two ubuntu 9.04 machines:

```
rsync -av 192.168.0.1:/home/farsheed/projects/BurnCity/ /home/farsheed/Public
```


Could anyone help me to solve my problem. I know the directory exists.
Thanks in advanced.


There was an error in your syntax; you left out the ** ssh ** command along an **e** :)
Should be :

```
rsync -ave ssh 192.168.0.1:/home/farsheed/projects/BurnCity/ /home/farsheed/Public
```

---

### Post by rodmena on 2009-10-20
NO, as rsync 2.6, there is no need for -e ssh.
And ok, my problem solved. the folder name is **P**rojects not **p**rojects.

Thanks.

---

