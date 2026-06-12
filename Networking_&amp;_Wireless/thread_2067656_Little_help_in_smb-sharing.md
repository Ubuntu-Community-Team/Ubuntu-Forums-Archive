---
title: "Little help in smb-sharing"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by Azyx on 2012-10-07
Hi.
I have a deskop computer with 12.04 and I have shared some resources with samba by editing the /etc/samba/smb.conf
I did it because a wanted to share same folder with both read-only AND read and right priveliges and that was not able to do with the share options in Nautilus. I get help to do this by Morbius1 :)

[http://ubuntuforums.org/showthread.php?t=1852451](http://ubuntuforums.org/showthread.php?t=1852451)

Now I have find out that if I log out from my account and log in as anohter user (user account) are the samba-share still working :) It's not so stange I think, because the samba config are under /etc/samba/ in the system and not under /home/user I is just a user-account (can't run sudo and it being reported to admin ;) How do I mount the disks as 'read only' without sudo?

I can imaging problem if more than one user can write to the samba-share or the disk simultaneously, but are there a easy way to access the shared folder at least as read-only? I have some media-files on the computer I access from another computer, and I still want to have access, even if I don't log in or log in as another user from both machines



/Cheers

---

### Post by Azyx on 2012-10-26
Bump. Is there any unclear thing in my question? I want to share as soon  the computer starts without log in as I think it does, because the  sharing come from /etc/samba and not from anything in the /home folder. Or have I missunderstand something with right and multiiple users? I have not worked with multiple user before...

---

### Post by luvshines on 2012-10-26
> **Azyx said:**
> Bump. Is there any unclear thing in my question? I want to share as soon  the computer starts without log in as I think it does, because the  sharing come from /etc/samba and not from anything in the /home folder. Or have I missunderstand something with right and multiiple users? I have not worked with multiple user before...

I think what you need is to add the CIFS share mount in fstab so that it's mounted after login
Since I have never personally used it, so can't help you with exact details, but I have seen multiple threads discussing this in this forum

---

### Post by Azyx on 2012-10-28
> **luvshines said:**
> I think what you need is to add the CIFS share mount in fstab so that it's mounted after login
Since I have never personally used it, so can't help you with exact details, but I have seen multiple threads discussing this in this forum

Off course, it need to mount before it can share, will test soon. :)

/Cheers

---

