---
title: "Preserving timestamps on CIFS mounts?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by yther on 2009-02-18
Hi, on my laptop I have a few CIFS shares mounted for use where I work.  Today I noticed I get errors when copying anything to these shares:

```
$ cp -p test.txt /mnt/bignas/share/Applications/
cp: preserving times for `/mnt/bignas/share/Applications/test.txt': Operation not permitted
```

If I copy the files from a Windows machine, the times are preserved.  Now, here's the ironic bit:

```
$ smbclient -L //bignas
Enter ____'s password:
Domain=[BIGNAS] OS=[Unix] Server=[Samba 3.0.24-1.22_OSSTECH]
```

The target device is a Buffalo NAS drive running some sort of Linux under the hood.  I get the same results copying to another NAS from GForce.

In my fstab, I have lines like this for the shares:

```
//192.168.2.104/share           /mnt/bignas/share       cifs auto,username=fred,_netdev,nobrl,noexec 0 0
```

I have tried adding the "noacl" option, with no change in behavior.  I found many problem reports on the web, but no solutions except that it was supposedly fixed many kernel revisions ago.  Any ideas if this can be fixed?

Thanks!

---

