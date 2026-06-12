---
title: "nfs-common restart does not work"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by maxideci on 2010-02-28
Hi, 
I am trying setup nfs mount points on my system.

when i try to restart nfs-common servic, I get following error.
[I]client :~ sudo /etc/init.d/nfs-common restart
bash: /etc/init.d/nfs-common: No such file or directory[/I]

apt-get install nfs-common gives this message :

[I]apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/I]

what am i doing wrong?
I'm running 
*Linux client 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux (karmic)*

---

### Post by suseendran.rengabashyam on 2010-03-02
Hi,

'nfs-common' is a package which contains NFS support files common to client and server, so the command sudo /etc/init.d/nfs-common restart will not work.

You can use the following command to list out the init files installed by 'nfs-common' package
```
dpkg -L nfs-common | grep /etc/init.d/
```

---

### Post by maxideci on 2010-03-06
> **suseendran.rengabashyam said:**
> Hi,

'nfs-common' is a package which contains NFS support files common to client and server, so the command sudo /etc/init.d/nfs-common restart will not work.

You can use the following command to list out the init files installed by 'nfs-common' package
```
dpkg -L nfs-common | grep /etc/init.d/
```

thanks a lot, there are many tutorials which instructed to do nfs-common restart. now its clear to me.

cheers!!

---

