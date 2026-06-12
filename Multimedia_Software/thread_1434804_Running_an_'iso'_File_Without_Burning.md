---
title: "Running an 'iso' File Without Burning"
date: 2010-03-20
forum: Multimedia Software
---

### Post by chome4 on 2010-03-20
Got some iso files and want to run them. Are there any programs around to make this task simple?

---

### Post by hxcobd on 2010-03-20
An ISO is a disc/CD image. You need a program to mount it virtually, or you have to burn it to an actual disc. You don't really "run" an ISO.

---

### Post by ShadowTek on 2010-03-20
If you're talking about playing a video, VLC will do it.

---

### Post by abohsin on 2010-03-20
You can mount the iso, like it is a CDROM, then see what you want to do with it:
sudo mkdir /media/cdrom
sudo mount -t iso9660 /path/to/iso /media/cdrom

Check if this works.

---

