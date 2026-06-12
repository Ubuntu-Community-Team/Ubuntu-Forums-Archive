---
title: "NFS permissions problem"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by lateralus01 on 2010-06-05
I'm trying to export the root filesystem of a network client on my ubuntu server through nfs. The client (running gentoo) is able to read the filesystem but not write to it.  I'm trying to configure the nfs server so the client can write to it too.

the server's ip is: 192.168.0.1
the client's ip is: 192.168.0.101

The filesystem is located on the server in /diskless/eta/ and all the files are owned by my user (mark).

```

root@mark-laptop:~# ls -l /diskless/eta
total 8932
drwxr-xr-x  2 mark mark    4096 2010-06-05 18:26 bin
drwxr-xr-x  2 mark mark    4096 2010-06-05 19:14 boot
-rw-r--r--  1 mark mark 9035360 2010-06-05 18:09 bzImage
drwxr-xr-x 10 mark mark   36864 2010-06-01 07:49 dev
drwxr-xr-x 32 mark mark    4096 2010-06-05 19:24 etc
-rw-r--r--  1 mark mark       0 2010-06-05 17:54 fastboot
drwxr-xr-x  2 mark mark    4096 2010-06-01 06:04 home
drwxr-xr-x  6 mark mark    4096 2010-06-05 18:26 lib
drwxr-xr-x  4 mark mark    4096 2010-06-01 07:48 mnt
drwxr-xr-x  2 mark mark    4096 2010-06-01 06:04 opt
drwxr-xr-x  2 mark mark    4096 2010-06-01 06:03 proc
drwx------  3 mark mark    4096 2010-06-05 19:21 root
drwxr-xr-x  2 mark mark    4096 2010-06-05 18:26 sbin
drwxr-xr-x  2 mark mark    4096 2010-06-01 06:04 sys
drwxrwxrwt  2 mark mark    4096 2010-06-05 19:16 tmp
drwxr-xr-x 12 mark mark    4096 2010-06-05 16:42 usr
drwxr-xr-x 12 mark mark    4096 2010-06-01 13:14 var

```

here's my configuration:

/etc/exports:
```

/diskless/eta 192.168.0.0/24(rw,sync,no_root_squash,no_subtree_check)

```

the configuration for the client is in pxegrub:
```

default 0
timeout 5

title=Diskless Gentoo
root (nd)
kernel /eta/bzImage ip=dhcp root=/dev/nfs nfsroot=192.168.0.1:/diskless/eta

```

A password is never supplied by the client but I never configured one, if that is the problem how do I configure nfs to allow write access without a password?

thanks,
lateralus01

---

### Post by irv on 2010-06-05
The ip address 192.168.0.1 sound like a router ip address? Are you sure that is the server ip?

---

### Post by lateralus01 on 2010-06-05
yes it is, my server is configured as a router and does NAT dhcp and dns

---

### Post by lateralus01 on 2010-06-06
i figured it out, i had to add rw to the client's configuration:

```

kernel /eta/bzImage ip=dhcp root=/dev/nfs rw nfsroot=192.168.0.1:/diskless/eta

```

seems stupid to me that this should have to be specified since a root filesystem is useless if you can't write to it...


lateralus01

---

### Post by irv on 2010-06-06
> **lateralus01 said:**
> i figured it out, i had to add rw to the client's configuration:

```

kernel /eta/bzImage ip=dhcp root=/dev/nfs rw nfsroot=192.168.0.1:/diskless/eta

```

seems stupid to me that this should have to be specified since a root filesystem is useless if you can't write to it...


lateralus01

I would almost agree with you that it sounds stupid, but Linux is much more secure than Windows and they cover all bases when it comes to security. And I am happy for that. Maybe that why I never use anti-virus software in Linux. Windows is a different story.

---

### Post by irv on 2010-06-08
lateralus01 why don't you mark this thread as solved. Just use the Thread Tools at the top of the page to do this.

---

