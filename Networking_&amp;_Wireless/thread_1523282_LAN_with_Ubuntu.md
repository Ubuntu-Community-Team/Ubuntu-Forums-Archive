---
title: "LAN with Ubuntu"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by sonon_b on 2010-07-03
Hi!
(1)  I m new to Ubuntu. I kinda like its feel-n-look but find difficult at times in handling it.
(2)  I have 11 PCs running Win-XP with peer-to-peer connectivity (workgroup) for my small office.
(3)  Now, I plan to change/migrate everything to Ubuntu only.
(4)  I started with 2 PCs and installed Ubuntu on them and they are pinging each other. It seems the physical connectivity is fine. However cant find/see them through NETWORK window on Ubuntu.
(5)  I wish to implement Ubuntu for my small office.
(5)  Is it possible to do the same thing (like windows workgroup) with Ubuntu ?
(6)  If so, how ?
(7)  Have googled to find something called NFS that might be of help but not sure on how to go about.

Any help is highly appreciated.

Regards,
Sonon_b

---

### Post by Iowan on 2010-07-03
To make Linux work with Windows, you will need Samba. [Here]("https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html") is a section of the Server guide that might be helpful.

---

### Post by gordintoronto on 2010-07-03
You might find it helps to change the workgroup name on your Ubuntu systems. It is stored in /etc/samba/smb.conf

Did you "share" a folder on either Ubuntu computer? I don't think it will appear in "network" until you do.

There is an excellent thread here on accessing Windows shares. However, if you intend to drop Windows completely, it is not relevant.

---

### Post by sonon_b on 2010-07-06
Hi!

Thanks for the prompt reply. 
However, let me rephrase the issue.
I wish to setup LAN with Ubuntu ONLY (NO WINDOWS). 
I have UnInstalled Windows from the computers and have Installed Ubuntu. 
Now I wish to share files across LAN as I used to do when in Windows.

Thanks in advance.

Regards,
Sonon_b

---

### Post by Iowan on 2010-07-06
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is a How-To for NFS, and [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is a help page.

---

