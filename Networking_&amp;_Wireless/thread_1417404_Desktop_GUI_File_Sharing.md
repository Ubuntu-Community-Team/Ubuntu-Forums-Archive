---
title: "Desktop GUI File Sharing"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by dbrine on 2010-02-27
I just installed 9.10 and I tried to share specific folders by right clicking and selecting share. Not a problem. 

However when I goto a Windows machine I see the share but cannot connect, says incorrect login/ password. I used the same login/ pass for the linux box and I created a new user and I still get the same results. What am I doing wrong??

I want to use the GUI for this please. When I edit the smb.conf I don't see the share.


thanks,

---

### Post by Iowan on 2010-02-27
> **dbrine said:**
>  When I edit the smb.conf I don't see the share.Nautilus shares are kept in a different place - check 
[/var/lib/samba]("http://http://ubuntuforums.org/showpost.php?p=7369157&postcount=4")

---

### Post by dbrine on 2010-02-27
found it. I see the shares but I still can't access them, no permissions?

---

