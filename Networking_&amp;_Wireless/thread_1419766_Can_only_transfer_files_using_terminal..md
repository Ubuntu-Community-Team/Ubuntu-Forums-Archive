---
title: "Can only transfer files using terminal."
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Karakh on 2010-03-02
I have an SMB NAS mounted using CIFS, and can transfer files quite easily using the terminal, but if I try to copy/paste files using Nautilus or Thunar it almost always fails with an input/output error.

No errors when transferring files from Windows 7, XP, or OSX, so I'm guessing that the problem lies in the way I'm mounting it in Ubuntu. Here's the relevant fstab line:

```
//192.168.1.100/Main /media/shared cifs guest,rw,nounix,noserverino,uid=1000,gid=1000,iocharset=utf8,codepage=unicode 0 0

```

Any ideas?

---

### Post by suseendran.rengabashyam on 2010-03-02
Hi,

A similar thread
[http://ubuntuforums.org/showthread.php?t=1399674](http://ubuntuforums.org/showthread.php?t=1399674)

Hope this helps.

---

