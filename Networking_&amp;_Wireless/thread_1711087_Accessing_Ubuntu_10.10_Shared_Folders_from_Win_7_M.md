---
title: "Accessing Ubuntu 10.10 Shared Folders from Win 7 Machine"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by knightysmith on 2011-03-20
Morning team, 

I have a Windows 7 (64 bit) PC and an iMac that are unable to access shared folders on a Ubuntu 10.10 machine. I have set the folder share permissions to allow access to anyone, and also shared the entire drive through Samba.

The bizarre thing is that if I share a folder on the system hard drive (i.e downloads, movies etc), I can access them from the Win7 machine and the iMac, but if the shared folders are on the second hard drive of the Ubuntu machine, than no luck.

Apologies if that is confusing. In a nut shell, the shared folders on a second hard drive of the Ubuntu machine can be seen but not accessed by the Windows 7 PC or the iMac.

Thanks for your help peeps, much appreciated.

---

### Post by knightysmith on 2011-03-21
[tumbleweed...]

---

### Post by Morbius1 on 2011-03-21
This doesn't sound like a Samba problem - it sounds like a Linux file permissions problem.

If you created a guest share and you want the remote users to read only then the permissions on the target directory have to be 755. If you want write access then it has to be set to 777.

Unfortunately, from you description we don't know what method of samba you are using ( there are 2 ), how the other "drive" is formatted, or if the other drive is mounted automatically on boot.

You might want to post the output of the following commands so we can first see how samba is set up:
```
net usershare info --long
testparm -s
```

---

### Post by knightysmith on 2011-03-21
All sorted thank you. 

The issue was that I had unmounted NTFS drives with a space in the label name. Mounted, changed label name, all fixed.

---

