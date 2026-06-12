---
title: "Networking 2 Ubuntu PC's"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Norster on 2009-04-26
I have a laptop with Ubuntu 9.04 only, and a PC dual boot Ubuntu 9.04 and windows XP (on separate hard drives).

The laptop, and the PC when in Ubuntu mode, can both see the windows hard drive and files.

The laptop, and the PC when in Ubuntu mode, cannot see each other. Both can use the wireless internet at the same time.

Can anyone help me get the 2 Ubuntu installations to see each other ?

---

### Post by Iowan on 2009-04-26
> **Norster said:**
> The laptop, and the PC when in Ubuntu mode, cannot see each other.Can they **ping** each other? Are they in the same subnet?

---

### Post by Norster on 2009-04-26
Hi, Iowan,

Yes, I can ping either from each of them.

---

### Post by Iowan on 2009-04-26
> **Norster said:**
> The laptop, and the PC when in Ubuntu mode, can both see the windows hard drive and files.
I presume this meant PC in Windows mode. 
Ubuntu comes with clients for SSH and Samba (maybe another one or two), but to share FROM the machine usually requires installing the server portion. How/what do you plan to share - or maybe I'm misunderstanding what you mean by "cannot see each other"

---

### Post by Norster on 2009-04-27
Hi,

The PC is not in Windows mode, but running Ubuntu.

I would like to be able to see either Ubuntu installation from the other one, and maybe copy/transfer files between them.

I'd like to be able to do this using the desktop, rather than at a prompt level.

If the PC is running in Windows mode, I can see either installation and share files.

My problem is when 2 Ubuntu installations are running.

---

### Post by Almighty on 2009-04-27
you might need to install NFS

```
 sudo apt-get install nfs-common 
```

I didn't think you still had to do that, but it could solve your issue.

---

### Post by stchman on 2009-04-27
> **Norster said:**
> I have a laptop with Ubuntu 9.04 only, and a PC dual boot Ubuntu 9.04 and windows XP (on separate hard drives).

The laptop, and the PC when in Ubuntu mode, can both see the windows hard drive and files.

The laptop, and the PC when in Ubuntu mode, cannot see each other. Both can use the wireless internet at the same time.

Can anyone help me get the 2 Ubuntu installations to see each other ?

Easy, use NFS.  Forget Samba.

Follow my tutorial.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

---

### Post by theozzlives on 2009-04-27
> **stchman said:**
> Easy, use NFS.  Forget Samba.

Follow my tutorial.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

You need SAMBA to see Windows!

---

### Post by stchman on 2009-04-28
> **theozzlives said:**
> You need SAMBA to see Windows!

The title of the thread was "Networking 2 Ubuntu PCs".  His one PC dual boots but both run Ubuntu 9.04.

---

### Post by Norster on 2009-04-30
Thanks to all who replied.

Some ideas for me to try.

---

