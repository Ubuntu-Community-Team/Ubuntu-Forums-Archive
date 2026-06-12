---
title: "Android can browse but not read/write files on ArchLinux Samba share"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by konradsa on 2013-03-17
Hi,

A little bit of topic, but I am hoping some knowleadgable people can help me here.

I got a strange problem when trying to access files on a Linux samba share using my Nexus 7, running Android 4.2.2. The share is on a Pogoplug running ArchLinux and I can access it from Xubuntu and my iPhone fine. Howerver, on the N7 using ES File Explorer, i can browse the directories and I can even create new files. But as soon as I try to access a file (read or write) I get an error saying "parameter incorrect" or "Cache remote file failed". The problem occurs on public shares as well as user shares. The shares are set to writable, and like I said, reading/writing works fine from my laptop and iPhone.  I tried other Samba clients than ES File Explorer, but the result is always the same. 

Anybody an idea how to solve this? Are there some known Samba configuration options that are required for or incompatible with Android?

---

### Post by konradsa on 2013-03-17
Btw, just tried to browse a Windows 7 share from my Nexus 7 and that works fine. So there must be something specific to the ArchLinux Samba configuration that the Nexus doesn't like.

---

### Post by konradsa on 2013-03-17
Found the solution, this appears to be a Samba bug: [https://bugzilla.samba.org/show_bug.cgi?id=9706](https://bugzilla.samba.org/show_bug.cgi?id=9706)

Setting unix extensions = no in the smb.conf fixes it for now.

---

