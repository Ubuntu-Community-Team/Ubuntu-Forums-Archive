---
title: "Samba share with guest access from USB drive"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by dumbmatter on 2011-03-05
Ubuntu 10.10 here.

I have used the built-in right click menu to share files via Samba. It has worked perfectly every time until now. I want to share a folder on a USB hard drive. The folder shows up in the network, but when I click it (from any computer), it says "Failed to mount Windows share".

I found [this post](http://ubuntuforums.org/showpost.php?p=10328139&postcount=3) which suggests it has something to do with guest access. Indeed, when I disable guest access, it all works fine. But even implementing the solution I linked to for guest access (setting "force user = your-user-name" in smb.conf) didn't fix it for guest access. I still get "Failed to mount Windows share" unless I require a username/password.

Any ideas?

---

### Post by 8dogsbarking on 2011-03-09
I am having the same problem.  I have a desktop running 10.10 with a shared usb drive, and I can connect a Windows 7 laptop to a shared usb drive just fine.  But when I try to connect my macbook pro, I can see the desktop ubuntu computer, but it says that I can't mount the shared drive.  Other times is says it can't connect because the origional item for "drive" can not be found.  I could sure use some help.

---

