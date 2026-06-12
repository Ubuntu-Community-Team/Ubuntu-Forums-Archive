---
title: "Help - Problems Networking 2 Ubuntu PCs!!"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by thedonkster on 2009-05-03
OK, so I made the full switch from Windows and I now run two Jaunty PCs.  The desktop PC connects to the wireless router by cable.  The laptop connects wirelessly.  Both connect to the internet without problems

For the life of me I can't share folders between the two computers.  I have created a dummy shared folder on each Ubuntu desktop - but neither computer can access the shared folder of the other.

I installed SAMBA - but I'm not even sure this is right because I think samba is for networking with Windows?  Now when I click on 'Places', 'Network' - I have a 'Windows Network' that I'm unable to mount!! (And there's not a Windows PC in sight!!)

I love Ubuntu - but I'm sure creating a network was much easier in XP (and I really don't want to have to go back!!)

All help appreciated - thanks...

---

### Post by Iowan on 2009-05-04
Samba is the preferred way to share files between Ubuntu and Windows - but it can work between Ubuntu boxes as well... although NFS is the "standard". SSHFS is yet another option.  Perhaps a few links to further cloud the issue...
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

BTW, [here]("http://ubuntuforums.org/showthread.php?t=1148446") is a similar thread...

---

