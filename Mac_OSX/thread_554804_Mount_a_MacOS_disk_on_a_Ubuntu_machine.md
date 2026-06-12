---
title: "Mount a MacOS disk on a Ubuntu machine?"
date: 2007-09-19
forum: Mac OSX
---

### Post by ggravier on 2007-09-19
Hi!

I have a MacOS disk that I need to get files of. But the Mac is dead. Fortunately, I have a Ubuntu laptop.

Methinkst that MacOS is close to BSD... and hopes that the filesystem from MacOS should be visible in Linux... Is that the case? Will Ubuntu be able to see it? Any suggestions / recommendations before I plug things in?

Cheers,
Gilles.

---

### Post by twocargar on 2007-09-19
I can read my Mac OS partition on my Linux box fine with Feisty, and I belive it worked the first time I used it.  The partition mounts as read-only, hfs+.

Good luck,

TCG

---

### Post by elvis on 2007-09-19
MacOSX by default can use UFS, HFS or HFS+.  HFS+ is the default choice by MacOSX and most users.

Install the packages "hfsplus" and "hfsutils", and you'll be able to mount the drive and recover your data.

---

