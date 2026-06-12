---
title: "Mounting SAMBA shares, which are not available all the time"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by xfuser4 on 2009-11-06
Hello,
I have two computers in a home network: one computer runs Ubuntu 9.04, the other one runs Windows XP. I want to access the files of the Windows computer using any application on Ubuntu.

There are three options to do this:

1. Using Nautilus with an "smb://"-Path. The problem with this approach is, that I can't access the shares from the Open-Dialog in GNOME applications, since they are not displayed as mount points and I can't mount them from the open dialog.

2. Using a permanent entry in /etc/fstab. This won't work, since the windows computer is not always up (especially the Ubuntu computer might boot even if the windows computer is down).

3. Using autofs. This works with several drawbacks: there are delays of 1-5 seconds when accessing the SMB share. Even if I specify a timeout for the autofs of 1s, this leads to a slowdown of all applications if they access a folder that is nearby the autofs mount point.


Is there any other way to:

- *automatically* mount SMB shares accessible for *all* applications (not only Nautilus)
- has no problem, that the windows share might not be available all the time (esp. at boot time of Ubuntu!)
- does only produce delays when I access the share directly...

---

### Post by andrewc6l on 2009-11-06
I'm not sure why you don't want to use /etc/fstab. I have a 9.04 box that tries to mount a nonexistent server (some day I'll get that server back online) and it seems to boot up just as quickly as it would if the server were there. I'm mounting as cifs, I think.

The plus to that is you can just mount -a if you bring your Windows server up after booting your Linux box.

---

### Post by xfuser4 on 2009-11-08
The problem on the /etc/fstab-variant is, that you have to mount the SMB share manually (using mount -a, as you said), if the Windows server was not online during boot.

The ubuntu machine is used by a person that wants to migrate from Windows to Linux. From Windows he is used not to mount SMB shares manually - since Windows will mount it automatically when clicking on a remote SMB folder...

Also there is another problem with /etc/fstab: if the Windows server goes down later on, the access to the parent directory of the mount point using Nautilus might slow down for a while, since Nautilus tries to crawl the mount point...

---

