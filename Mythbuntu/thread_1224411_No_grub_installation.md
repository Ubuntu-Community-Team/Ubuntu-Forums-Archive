---
title: "No grub installation"
date: 2009-07-27
forum: Mythbuntu
---

### Post by jgauthier on 2009-07-27
All,

 I'm doing a clean install on MB 9.04.  After 3 or 4 installs, I realized that grub is not installing.   I went through the partitioning carefully, my root system is ext3, and under "Advanced" I made sure that "Install Boot Loader" was selected.

I booted off the Live CD and installed grub with 
```
install-grub --root-directory=/mnt /dev/sda
```

I realized that did not create a menu.lst, so I fashioned one.. but it didn't work.   I didn't create it correctly, I guess.

Needless to say, I don't want to have to create it.  What's going on?  How can I get grub to install during the setup?

Thanks!

---

### Post by jgauthier on 2009-07-27
Additionally,  I'm trying to fix this, and find that /initrd is a broken symlink.  There is no initrd in /boot.

What is going on here?

---

### Post by Choose on 2009-07-27
> **jgauthier said:**
> All,

I booted off the Live CD and installed grub with 
```
install-grub --root-directory=/mnt /dev/sda
```



when you installed grub did you specify the location you wanted to install it (e.g) /dev/sda1 ?

---

### Post by jgauthier on 2009-07-27
Yes, that is in the text above.  I installed it to /dev/sda.

---

### Post by jgauthier on 2009-07-27
okay, so I was doing a manual partition scheme.  I read that ubuntu defaults to ext4.  Well, guess what?

The installation silently fails when you make your root partition ext3.  Real nice.  Shame on Ubuntu :(

I ran through the same exact process, only selecting ext4 instead of ext3, and lo' and  behold.  I have an initrd, and grub installed.

If it's not going to work, it shouldn't let me do it. Period!

=)

---

