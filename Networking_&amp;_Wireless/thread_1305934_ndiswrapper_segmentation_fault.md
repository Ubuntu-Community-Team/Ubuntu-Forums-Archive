---
title: "ndiswrapper segmentation fault"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by irishbreakfast on 2009-10-30
I can't get ndiswrapper to work in karmic.
I used dpkg to install the version with the install disc. But all I get are Segmentation faults.

[INDENT]$ndiswrapper -v
Segmentation fault
Segmentation fault
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
Segmentation fault

You may need to upgrade driver and/or util to latest version available at ..
[/INDENT]
So I went and got v1.53 and 1.55. Neither will compile.

What do I need to do to fix this?

---

### Post by irishbreakfast on 2009-10-31
On a whim I reinstalled 9.10, the only difference being that I changed / from ext4 to ext3. Now ndiswrapper works perfectly. One thing solved. 

I restarted and then the filesystem would not mount.

I ran fsck on / and there was a problem with the date in the Superblock. (I noticed the date on the desktop was wrong sometime during fixing ndiswrapper but left it till later) fsck kindly asked if it could fix the date. I replied 'y' and it did, the rest of the partition was OK. 

I restarted and 9.10 started up fine.

---

### Post by MCunha on 2009-12-30
Hi,

Anybody found a solution to this issue?
I can't compile ndiswrapper-1.55 in Karmic:

```
In file included from /root/ndiswrapper-1.55/driver/crt.c:16:
/root/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/root/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/root/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/root/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/ndiswrapper-1.55/driver'
make: *** [all] Error 2
```

And if I install it with apt-get will not work. Everything will return "Segmentation fault" :(

Thanks in advance.

---

