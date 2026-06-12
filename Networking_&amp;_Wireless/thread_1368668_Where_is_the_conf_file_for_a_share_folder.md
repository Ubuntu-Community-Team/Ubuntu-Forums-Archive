---
title: "Where is the conf file for a share folder"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by snappy46 on 2009-12-30
I was wandering if anyone can tell me where is the conf file when you use share folder (using nautilus right click and share folder option).  I use to just modify my smb.conf file with the folders I wanted to share but it is much easier using nautilus and the click method.

So I used that click method to share 4 folders on my ubuntu machine.  I assume at that time that smb.conf must be change to reflect the folder I specified as shares.  I was surprised when I look at my smb.conf file to see that the content had not changed.

So my question is where is the change being made???  I know it works fine since those shared folder that I created are available to other devices (presently using it with my media player).  Just curious really and it would also be nice to know to make changes manually if required.

Thanks.

---

### Post by capscrew on 2009-12-31
> **snappy46 said:**
> I was wandering if anyone can tell me where is the conf file when you use share folder (using nautilus right click and share folder option).  I use to just modify my smb.conf file with the folders I wanted to share but it is much easier using nautilus and the click method.

So I used that click method to share 4 folders on my ubuntu machine.  I assume at that time that smb.conf must be change to reflect the folder I specified as shares.  I was surprised when I look at my smb.conf file to see that the content had not changed.

So my question is where is the change being made???  I know it works fine since those shared folder that I created are available to other devices (presently using it with my media player).  Just curious really and it would also be nice to know to make changes manually if required.

Thanks.

Nautilus uses GVFS user space libs for Samba shares.  The shares are located at /var/lib/samba.

---

### Post by snappy46 on 2010-04-21
Thanks a lot I did find my shares under /var/lib/samba/usershares.  Neat one more mystery solved.

---

### Post by Iowan on 2010-04-21
Wow - this thread has been open for awhile...
Is it finally [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

