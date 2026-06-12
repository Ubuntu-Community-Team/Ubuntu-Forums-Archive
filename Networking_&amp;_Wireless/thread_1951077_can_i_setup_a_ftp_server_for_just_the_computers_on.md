---
title: "can i setup a ftp server for just the computers on my router?"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by ElHippie on 2012-04-01
im running ubuntu 11.10, i just wanted a way to send some files and to my brothers windows pc. i thought a ftp server would be good, but i might be wrong. i was thinking like a drop box type of thing, sorry if this question sounds bad, but thanks in advance](*,)

---

### Post by papibe on 2012-04-01
Hi ElHippie. Welcome to the forums!

I would recommend using [Samba]("https://help.ubuntu.com/community/Samba") to share files. The easiest way is to:
[INDENT]Right click on the folder you want to share.
Select Share Folder.
Install Samba (maybe called Windows network support, or SMB).
[/INDENT]
After that you'll have the option "Sharing Options" if you right click the folder. There you choose the name and the permitions (read write for all).

You can see more details and pics [here]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/"). They are a bit old but the actual steps you should be very similar.

After that you'll be able to browse your Ubuntu directory on your Windows machine.

Hope it helps, and tell us if you need more help with that.
Regards.

---

