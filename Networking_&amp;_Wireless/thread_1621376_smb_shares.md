---
title: "smb shares"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by graylion on 2010-11-14
Hi guys

I am trying to connect to my samba server with xubuntu, so far with no luck.

I am trying to use fusesmb and have been following these instructions:

[http://ubuntuforums.org/showthread.php?t=300310](http://ubuntuforums.org/showthread.php?t=300310)

as well as these:

[http://forum.vectorlinux.com/index.php?topic=10471.0](http://forum.vectorlinux.com/index.php?topic=10471.0)

and these

[https://help.ubuntu.com/community/FuseSmb](https://help.ubuntu.com/community/FuseSmb)

the top ones say to use Applications - System - shared folders to setup smb client. Xubuntu maverick doesn't seem to have that menu point. So I copied the smb.conf from my desktop machine. libsmbclient is installed.

fuse as such seems to run since teh folder that i designated as mount point (~/Network) changes owner to root when i run fusesmb Network. But apart from that nothing happens.

help???

Thanks

---

### Post by Morbius1 on 2010-11-14
As I recall fusesmb has compatibility problems with smbclient so I don't think that will work. 

Applications -> System -> Shared Folders used to call shares-admin and I don't think that works any longer either.

If you want to share files to others I would suggest one of two different packages for the two different methods of creating samba shares:

Usershares: thunar-shares-plugin
> Thunar Shares Plugin allows you to quickly share a folder from
the Xfce Thunar file manager without requiring root access.Once installed just go into thunar, right click a folder you own, select Sharing, check all the boxes and you just created a samba usershare.

Classic-shares: system-config-samba
This is the more traditional way of creating a samba share.

As for connecting to a remote smb share I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

The instructions given are for automounting a remote share but you don't have to go to that extent if you don't want to. Gigolo is a samba browser, bookmarker, and auto mounter among many other things.

---

