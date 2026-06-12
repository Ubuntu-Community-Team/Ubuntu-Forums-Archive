---
title: "How to acess another computer with the local ip."
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by xZachtmx on 2009-11-22
I went into my router dhcp list and found the local ip to my laptop and it is running windows vista and i have ubuntu 9.10.  Is there a way to acess its files and even write to them from my computer?  I dont mean remote computer viewing i mean like commands i can use from the terminal to access the harddisk.

Sorry if this is an odd question but there dosent seem to be any linux tutorials on this only windows.

thanks for any help!:P

---

### Post by unamanic on 2009-11-22
You should be able to get to the computers files via Places->Network. You may have to set up sharing on the windows side, although I think the default c$ share should be there.  For anything not publicly shared, you'll need your windows user ID and password.

---

### Post by Iowan on 2009-11-23
Should be do-able - Ubuntu comes with Samba client pre-installed. [This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help with some problems. Author has another How-To in his signature for mounting CIFS (Windows) shares.

---

