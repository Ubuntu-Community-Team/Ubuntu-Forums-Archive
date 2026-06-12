---
title: "Cannot browse the files in Enhanced audio CD(s)"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by Turin Turambar on 2007-01-13
Whenever I insert the enhanced CD (CD that contains both audio & files) Ubuntu asks me what to do, however whenever I hit "browse" for files, it does nothing... 

So, basically, I cannot browse files on those CDs. Normally, everything is working fine in Windows................. :(

---

### Post by Turin Turambar on 2007-01-15
bump

---

### Post by warkro on 2007-02-12
i'm wondering as well...anyone know?

---

### Post by etienne.navarro on 2007-02-19
I have the same problem. I can't view the disc with fdisk either.
Also mounting it gives the error
```
mount: /dev/cdrom: can't read superblock
```

I have, however, managed to mount the disc. However, the two tracks appear all together.
```
sudo mount -t iso9660 -o ro /dev/cdrom /mnt
```

---

### Post by calculon102 on 2007-12-13
Hi, found this thead when I had the same problem on my Ubuntu 7.10 workstation. The enhanced cd I bought recently didn't want to play under Ubuntu, however I discoverd it had to be a problem with my DVD-ROM-drive. My Notebook with Ubuntu 7.10 recognized the DVD, also did my workstation with a very old CD-Burning-Drive. So problems with non-copy-protected CDs are usually related to your DVD-drive.

---

### Post by joshuapurcell on 2008-06-08
This is the most annoying problem I've come up against in a long time. I cannot believe this OS won't let me view the files on an audio CD. Here is a bug report that describes the problem:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/39345](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/39345)

Once I find a way to just do something as simple as view the actual files on a CD I'll post here... mounting the old fashioned way isn't working for some stupid reason.

I'm using gutsy 64-bit... I like how we are going backwards in features and (un)intelligently guessing that people only want to play music in some player instead of work with the files on the CD. Great.

---

