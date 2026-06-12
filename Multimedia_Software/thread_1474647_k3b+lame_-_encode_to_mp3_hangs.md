---
title: "k3b+lame - encode to mp3 hangs"
date: 2010-05-06
forum: Multimedia Software
---

### Post by CryptoPaul on 2010-05-06
Hi

Using k3b with ubuntu (not kubuntu) 10.04 i386 desktop.

When encoding file(s) to MP3, either 'ripped' or 'converted', using lame as an external encoder k3b hangs after the last file is encoded and it is necessary to force quit. The files are encoded and written to disk OK.


k3b: 1.91.0~rc2-0ubuntu3
K3b: External Audio Encoder Version 5.0
lame: 3.98.2+debian-0ubuntu3


Any ideas welcome - google did not seem to be my friend this time :(


Paul

---

### Post by shirsch on 2010-06-06
> **CryptoPaul said:**
> Hi

Using k3b with ubuntu (not kubuntu) 10.04 i386 desktop.

When encoding file(s) to MP3, either 'ripped' or 'converted', using lame as an external encoder k3b hangs after the last file is encoded and it is necessary to force quit. The files are encoded and written to disk OK.


Same exact (mis)behavior here. Kubuntu 10.04 x86_64 desktop.  K3b is clearly broken.

---

### Post by no2498 on 2010-06-06
this only a long shot im no coder 
try installing smplayer it loads a lot of new codes
type it in a terminal it tells you how to get it installed

hope this helps

---

### Post by CryptoPaul on 2010-06-08
This seems to be affecting several users now


I filed this bug report a while back...

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/576563](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/576563)

...which was then flagged as a duplicate of this...

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/576500](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/576500)

...where it is exhibiting the same behaviour when encoding to flac.

---

### Post by Kalrog on 2010-08-19
Well, sign me up as having this issue as well.

And on the bug listed earlier - it shows a fix released in a post currently 14 hours old:

This bug was fixed in the package k3b - 2.0.1-1ubuntu1

---

