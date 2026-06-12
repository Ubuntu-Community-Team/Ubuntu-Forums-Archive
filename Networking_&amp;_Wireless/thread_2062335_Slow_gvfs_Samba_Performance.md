---
title: "Slow gvfs Samba Performance"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by gnagfl0w on 2012-09-24
Hello,

if I use/acces a Samba Share using Nautilus or manually using "gvfs-mount smb://SERVER-IP/Share" I get a poor Performance, only about 7 mb/s on my 100 Mbit Network.

If I access the same Share on Windows I get Fullspeed 100 Mbit (About 11 mb/s), also if I mount using "sudo mount -t cifs //SERVER-IP/Share /mountpount" which uses cifs instead of gvfs I get fullspeed too, so can anyone tell me if there is a Performance Problem/Bug in gvfs or how gvfs is using SMB Shares differerently ?

I tested read Perfomance (From my Network Samba Share) with multiples files and always, the cifs-Version is fullspeed and the GVFS-Version has some mb/s less.

After some research I found some tips to optimize the Samba Settings of my Ubuntu Installation and some network tuning tips, but as the CIFS mounted share gets the full Network Speed I don't believe its that kind of problem.

---

### Post by gnagfl0w on 2012-09-29
Can nobody reproduce the Problem or help me out in any way ?

---

### Post by db260179 on 2012-09-30
I'm afraid you are not the only one who has noticed this.

I use smb4k to mount my shares as the gvfs-smb implementation is screwed.

smb4k - 81mb/s, nautilus - gvfs - 31mb/s (rubbish)

> **gnagfl0w said:**
> Can nobody reproduce the Problem or help me out in any way ?

---

### Post by kjhermans on 2012-11-30
The issue seems to be host resolution. Try hard-configuring the appropriate mappings in /etc/hosts.

---

