---
title: "Sharing the Windows drive of a Dual boot machine through Samba."
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by jwbrase on 2009-04-18
My Linux box dual boots Ubuntu and Windows. I'm wanting to make data on my Windows partition available to the other computers on our network (which all run Windows only), via Samba when the machine is booted into Linux. I am a bit confused, though, as to what the "create mask" and "directory mask" in smb.conf should be. 

I understand the basic concept involved as far as the Linux side of things is concerned, 777 is rwx permissions for everybody, 755 is rwx for owner, and a prescription (r-x :-)) for everyone else, etc. What I'm not sure of is how this will interact with Windows/NTFS via Samba and what side effects I might get if I set things wrong. 

Despite having used Windows for years and Linux only for a few months, I'm actually more familiar with the permission structure of Linux, and since my files are going from an NTFS drive primarily used by the Windows side of this machine, being read by Linux and passed through Samba to machines running Windows, I'm not sure exactly what is happening permission-wise on the Windows side. Can anybody clarify things for me? Can I most likely just leave it as the default (create mask = 0644 directory mask = 0755), or will that cause problems?

---

### Post by superprash2003 on 2009-04-19
is your WINDOWS NTFS partition mounted in ubuntu?

---

### Post by jwbrase on 2009-04-20
> **superprash2003 said:**
> is your WINDOWS NTFS partition mounted in ubuntu?

Yes. Now I'm trying to set things up so that the shares on that partition are accessible from the network no matter which OS is booted. I've actually run into a bit of trouble getting that to work, so the original question is actually on hold at this point, being more of a security/administration issue than a works/doesn't work issue.

So far I've followed this tutorial: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

and gotten to the point where our other desktop can see the Linux box when it's booted into Ubuntu, but can't seem to see any of the shares on it.

---

### Post by superprash2003 on 2009-04-22
that could be due to the nautilus bug. try this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

