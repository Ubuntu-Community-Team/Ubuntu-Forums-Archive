---
title: "Does Samba's lack of SMBFS and gain of CIFS change anything for the end user?"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-01-27
I run Samba at home. I have my drives automatically mounting by their UUID which I placed in /etc/fstab.

Previously, I simply used the mount command to mount them. "sudo mount /dev/sda1 /media/backup" etc...

I think (well, I KNOW) I'm probably mistaken here... but can someone clarify this for me? Does Samba using CIFS more and not so much SMBFS make a difference to someone like me? What does it change? Is the change in the background, where even network administrators won't notice the difference?

I'm under the impression that it's a network file system which runs in the background. I work in IT, and unfortunately we run all Windows servers, but I'm curious as to what the setup truly is with SMBFS and CIFS and how it effects the end user.

---

