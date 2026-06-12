---
title: "Setting up file sharing"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by maxpathan on 2009-12-15
I have a desktop top running UBUNTU 8.04 physically connected to a wireless-router. I also have a laptop, which is wireless. The laptop dual boots to Vista and UBUNTU 9.04

How do i set up a network to share files?

Regards
Max

---

### Post by Iowan on 2009-12-15
Some filesharing options are listed in [this]("http://ubuntuforums.org/showpost.php?p=8487983&postcount=4") post.  For Windows sharing, you'll need [Samba]("https://help.ubuntu.com/community/SettingUpSamba").

---

### Post by gordintoronto on 2009-12-16
Everything is described in many posts in the forums.

To set some context: the easiest thing is to have a shared folder on the desktop.  You need to make sure all three environments use the same workgroup, and my preference is to have it be unique, such as "maxnet".  Put a file into the shared folder so you will know if you got there.  From the laptop under Ubuntu, begin with Places/Network and double-click until you get to the folder.  For Windows, begin with "network places."

In Ubuntu, the workgroup is stored in /etc/samba/smb.conf  
You can edit it with
```

gksudo gedit /etc/samba/smb.conf

```

In Windows, the workgroup is one of the properties of "My Computer."

File sharing seems to become ten times more difficult when there are firewalls in the picture.

---

### Post by Iowan on 2009-12-16
For the client-side of Samba, [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might be useful.

---

