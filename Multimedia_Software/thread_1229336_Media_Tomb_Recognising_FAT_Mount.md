---
title: "Media Tomb Recognising FAT Mount"
date: 2009-08-02
forum: Multimedia Software
---

### Post by catnthehat on 2009-08-02
G'day All,  I have set up Media Tomb but I cannot get it to detect my "/windows" mount. I read that this might be due to permissions and indeed, /windows does not have read permissions for others, but I cannot seem to set the right permissions. Commands like sudo chmod +r /windows don't change the permissions.  The file attributes are: drwxrwx--- 1 root plugdev 12288 2009-07-26 18:20 /windows/  Any help appreciated, thank-you.   Regards, catnthehat

---

### Post by coogur on 2009-10-04
I remember reading up on this, it`s not the actual file/directory permissions but how the partition is mounted.  look up your etc/fstab file for existing /windows mount point permissions.

Ubuntu forum as a section detailing how to properly mount FAT partitions.
Hope this helps.

---

