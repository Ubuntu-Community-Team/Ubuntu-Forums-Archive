---
title: "Samba, Ubuntu, Natilus Write Access."
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by rxbandit on 2006-06-27
I have Ubuntu up and running. I have a server hosting all my files running headless running Fedora Core 4. I want to be able to edit file names and such using Natulis. But also at the same time i don't want all the windows computers in the house to have write access. Right now everything is working fine with my samba set up except, i would like for my ubuntu box to have write access on the fedora core Samba shares. I have them mounted in my fstab using smbfs. I've searched but i can't seem to find any info to help me.

thanks for any help you guys can give me.
rx

---

### Post by mogelhead on 2006-07-11
It sounds like you should setup two different samba users on your Fedora Core 4 box, USER_R with only read persmissions and USER_RW with both read and write permissions. And then from your Windows computers connect to the samba share with USER_R and from your ubuntu box connect with USER_RW.

---

