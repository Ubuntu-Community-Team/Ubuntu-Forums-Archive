---
title: "[PROBLEM] How Do I access SMB shares in Mythbuntu?"
date: 2008-08-20
forum: Mythbuntu
---

### Post by ryanlhjess on 2008-08-20
Good Day

I have several windows computers on a home network that have various videos that I would like to be able to access in mythbuntu.  How do I setup mythbuntu to be able to access these shares?

Thank you.

---

### Post by LarryJ2 on 2008-08-20
Hi Ryan
Your question is really two in one.  The first is, how do I mount the SMB/CIFS shares available from your various PCs onto your mythbuntu box. Once mounted, these remote shares will be available from within the file manager (thunar, nautilus etc) on your mythbuntu box.  To mount these shares, thereby making them appear in the mythbuntu file manager,  I use **pyneighborhood** available from the repository.  It will take a little time to get used to pyneighborhood's gui.  I use many times per day to temporarily mount and dismount smb/cifs shares on my home network.  If you want the shares to appear permanently, then an entry in the mythbuntu box's /etc/fstab may be the route to follow.

Then you can work on the second question.  How do I access mounted shares from within mythbuntu's gui.   I'm not certain how that's done.

Larry

---

### Post by ian dobson on 2008-08-20
Hi,

For the second question.

If you setup mythvideo to use a specific directory for example /mnt and then create mounts to your windows servers under /mnt then you can browse them. For example:-

/mnt/server1 -> \\server1\videos
/mnt/server2 -> \\server2\myvideos

Regards
Ian Dobson

---

### Post by newlinux on 2008-08-20
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I recommend using CIFS.

And then, as mentioned you can specify the directory you want to access video files in mythvideo. You can specify multiple directories by separating them with a colon in the video path field in the mythvideo setup.

---

### Post by Loaded.len on 2008-08-20
Just a note... If after you've got your shares mounted and sorted out in Mythtv you find that your network is too slow (BTW: if you're not on gigabit ethernet, I wouldn't bother) you can try turning off Samba logging.  Sped my transfer rates up quite a bit.

---

### Post by newlinux on 2008-08-20
I'm not on gigabit ethernet (none of my switches are, and half of my NICs aren't) and I stream everything for HD mpeg-2 over the network (CIFS and through myth) just fine. Fast ethernet for most should at *least* reach 30Mbps, which is plenty for most streams, unless you have a lot of other network traffic on the same line...

---

