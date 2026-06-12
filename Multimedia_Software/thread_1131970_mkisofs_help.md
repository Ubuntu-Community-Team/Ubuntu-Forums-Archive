---
title: "mkisofs help"
date: 2009-04-21
forum: Multimedia Software
---

### Post by akd_inc on 2009-04-21
I am trying to make some custom boot dvds. but i can not figure out all the commands for mkisofs. i want to make a bootable iso from a folder i have on my desktop. it will be a boot disk for windows systems(dos) is there any gui frontend that makes it easier to do this? or can someone help me with the flags needed?
when i do a
mkisofs -o boot.iso /place/where/folederis  (found on a forum)
it makes an iso but it puts :1 at the end of all file names.

---

### Post by stilling on 2009-04-21
> **akd_inc said:**
> I am trying to make some custom boot dvds. but i can not figure out all the commands for mkisofs. i want to make a bootable iso from a folder i have on my desktop. it will be a boot disk for windows systems(dos) is there any gui frontend that makes it easier to do this? or can someone help me with the flags needed?
when i do a
mkisofs -o boot.iso /place/where/folederis  (found on a forum)
it makes an iso but it puts :1 at the end of all file names.

To create a bootable ISO for an operating system install such as Windows (handy for those virtual machines), provided you have a boot.img and the relevant i386 files:

cd root/of/your/files
mkisofs -b boot.img -no-emul-boot -boot-load-seg 1984 -boot-load-size 4 -iso-level 2 -J -joliet-long -l -D -relaxed-filenames -N -V NRMSVOL_EN -v -x .DS_Store -o ../Win2K3.iso .

To create a backup of the production log files you are busily examining:

mkisofs -iso-level 2 -J -joliet-long -l -D -relaxed-filenames -N -V NameOfBackup -v -x .DS_Store -o ~/Desktop/NameOfBackup.iso .

---

