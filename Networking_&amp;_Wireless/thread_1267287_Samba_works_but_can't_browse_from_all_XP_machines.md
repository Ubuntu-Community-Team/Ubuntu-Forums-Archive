---
title: "Samba works but can't browse from all XP machines"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by ivensj on 2009-09-15
hello, finally became a forum member.  I have this samba/windows issue that I really need some help with.  Searches are turning up no fixes so far.  I have put together a Ubuntu 9.04 box and am trying to make it my primary file server and maybe other things down the road.  I had this server working great and accidentally left a ghost autoboot disk in the drive during a reboot :( so it reconfigured my working Ubuntu drive into an old XP build.  

So I have rebuilt the basics, have ssh, vnc, hamachi and samba configured.  Everything works great except Samba.  It seems to work from some machines but others are asking for a username and password.  Specifically my home desktop and laptops, both running Windows XP Media Center Ed.  The desktop worked fine before I screwed up the Ubuntu fileserver as I was syncing files to the samba share.  The laptop is dual boot with Ubuntu and I can browse the samba share from the Ubuntu laptop.  My work computer, XP pro and part of a Domain, can access the Samba share via Hamachi.  I also have a Windows 2003 server which sees the samba share as a workgroup computer and can access it, read&write files.  The desktop and laptop can see the samba share in My Network Places but when clicked on it continues to ask for a username and password.  None of the other computers linux or windows ask for a username and password. 

So this samba share is wide open so I am dumbfounded as to why these 2 computers are having this issue.  This worked fine until the rebuild.  Any suggestions?  

here is the excerpt from smb.conf at the bottom of the file.

[files]
 comment = serverU File Share
 path = /media/filestorage/files
 browsable = yes
 guest ok = yes
 read only = no
 creat mask = 0777

I have uninstalled Samba and reinstalled it.  I have compared the windows services between working XP machines.  I have played with some of the smb.conf settings, workgroup/no workgroup, security=user but that is about all.  Could there be some pointer in these 2 XP machines that is conflicting with this "new build" of the Samba Server.  The samba server has the same machine name and static IP address.

any help would be greatly appreciated.  

Jesse

---

