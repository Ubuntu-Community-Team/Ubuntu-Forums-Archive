---
title: "How can I make a USB Hard Drive accessed by everyone, even when logged out?"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by infocom on 2010-04-29
Hi

At the moment to get a hard drive connected and visible for a user, I need to connect it when logged in as that user.... if I log out and back in as someone else like root, they cant see it and dont have permission to access it. 

So do you know how I can have my external usb hard drive as a drive that anyone can access when they login? 

The reason is I use it for remote backups from another machine via SFTP. I have created a separate user to connect via SFTP. I need to login as that user to connect the drive to see it when I SFTP, and then I need to stay logged in. I dont want this user to always be logged in, I just want them to be able to access the drive when they login via SFTP. I also then want my main user to see the drive when they login to. 

Thanks

---

### Post by ktmom on 2010-04-29
I really don't know, but I'm thinking that if it's not automounted, but mounted as part of fstab, it would still be mounted after you log out.  I think this thread may be helpful [http://www.linuxquestions.org/questions/ubuntu-63/automount-permissions-for-external-usb-hhd-555022/](http://www.linuxquestions.org/questions/ubuntu-63/automount-permissions-for-external-usb-hhd-555022/)

---

### Post by Iowan on 2010-04-29
> **infocom said:**
>  Now I need to find out how to make a USB hard drive accessible to everyone even when logged out and not just the logged in user.

[This]("http://ubuntuforums.org/showthread.php?&t=283131") might be a starting point.

---

