---
title: "minidlna storage: best practices?"
date: 2013-07-10
forum: Multimedia Software
---

### Post by Byb on 2013-07-10
Hi all
My PC crasched so I had to reinstall all.
At install time with the wizard I made a dedicated partition to store a minidlna folder for media files:
```
sudo cat/proc/mounts 
...
/dev/sdh2 /srv ext4 rw,noatime,data=ordered 0 0
...
ls -la /srv
total 24
drwxr-xr-x  3 root root  4096 juil.  4 21:47 .
drwxr-xr-x 22 root root  4096 juil.  5 08:08 ..

```

I remember it was borring to move files in /srv/minidlna because I had not priviledges for the folder and minidlna service runs with its own user:
```

id  minidlna
uid=115(minidlna) gid=125(minidlna) groupes=125(minidlna)

```

So I will sudo mkdir /srv/minidlna 
but which must be the priviledges on the folder so that I can move files to it without sudo and minidlna is allowed to use it?
For long time we lost a GUI to manage groups in ubuntu and command line are far too difficult in this matter so I'm afraid I will break something and don't know what so can't reverse if ever possible.

Thanks for help
bye bye

[Edit] please at least a yes or no: is this the good way?:
```

 ls -la
total 28
drwxr-xr-x  4 root root      4096 juil. 10 23:48 .
drwxr-xr-x 22 root root      4096 juil.  5 08:08 ..
drwx------  2 root root     16384 juil.  4 21:47 lost+found
drwxr-xr-x  2 me  minidlna  4096 juil. 10 23:48 minidlna

```

---

