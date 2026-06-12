---
title: "Can't install bootloader"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-01-21
Hi all,

Past couple of iso images have some bug which makes grub installation fail. It has an option to skip its installation. How can i install grub later? It seems to mess up with existing grub and i end up with grub rescue>.

What do you guys usually use ISO or alternate image to install ubuntu? There have been lots of crashes in the recent ISO images - ubiquity, ubi-partmen, bootloader installation and installer crashes itself.

Thanks.

---

### Post by wilee-nilee on 2011-01-21
> **soham_1207 said:**
> Hi all,

Past couple of iso images have some bug which makes grub installation fail. It has an option to skip its installation. How can i install grub later? It seems to mess up with existing grub and i end up with grub rescue>.

What do you guys usually use ISO or alternate image to install ubuntu? There have been lots of crashes in the recent ISO images - ubiquity, ubi-partmen, bootloader installation and installer crashes itself.

Thanks.

Personally I just wait to get a good ISO that will boot after installing. Reloading grub to the mbr is easy, and if you are dual booting Linux you can reload it and leave the stable one in control. There have been a few grub upgrades in Natty lately though.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I believe you can skip the grub install and follow this guide to mount the stable OS and reload its grub to the mbr, at least thats what I have seen on the forums. I have never done this myself though.

---

### Post by garvinrick4 on 2011-01-21
#This is the version I have in natty now:
grub-install (GRUB) 1.99~20110112-1ubuntu1
#If you choose not to install grub at install:
I believe you would have to use live cd and chroot with internet access into natty 
and its repositories and install grub-pc and grub-common that way to get 1.99

---

### Post by dino99 on 2011-01-21
> **garvinrick4 said:**
> #This is the version I have in natty now:
grub-install (GRUB) 1.99~20110112-1ubuntu1
#If you choose not to install grub at install:
I believe you would have to use live cd and chroot with internet access into natty 
and its repositories and install grub-pc and grub-common that way to get 1.99

Latest grub is now 1.99~rc1-1ubuntu1 from main server (updated about 10 hours ago)

---

### Post by donniezazen on 2011-01-21
Thanks, The problem was BTRFS. I am back on ext4 and grub installs just fine with it.

> **wilee-nilee said:**
> Personally I just wait to get a good ISO that will boot after installing.

How do you know if its a good ISO?

---

