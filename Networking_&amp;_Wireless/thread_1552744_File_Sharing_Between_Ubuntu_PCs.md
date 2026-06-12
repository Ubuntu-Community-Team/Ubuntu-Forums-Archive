---
title: "File Sharing Between Ubuntu PCs"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by clevertomato on 2010-08-14
I have searched about this in the forums and elsewhere. I know there is documentation about how to setup NFS, but it seems VERY involved. Before I invest the time into that, I have to ask... is there an easier way? I know "Linux is not Windows" but Windows is a common denominator for people... a point of reference... so I'm going to say that in Windows it's very very easy to setup basic file sharing and have it working in a few  minutes. Is there no equivalent option to that in Linux? Do I really have to make a list of what packages to install, install them, edit config files on both machines, etc? It's not that I can't do it, but if I have two Linux boxes and I just some quick file sharing in a trusted, home LAN environment, is there not a quick and easy way?

---

### Post by drdos2006 on 2010-08-14
I found this useful.


[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin because that was what I was using. If that does not work then on the Server machine:
sudo addgroup MyGroupName
Added /sharedfiles on server
Needed to change group permissions for /sharedfiles
sudo chgrp MyGroupName  /sharedfiles
//**
Client: Mounted /sharedfiles from terminal as /sharedfiles, can be set in /etc/fstab with :
sudo mount  <serverIPaddress>:/sharedfiles  /sharedfiles in /etc/fstab
Copied files as test and it worked.

---

### Post by YesWeCan on 2010-08-14
You don't need to use NFS.
The "Nautilus" application will do what you want with a couple of mouse clicks. Nautilus is the thing that provides the "Places" menu functionality. You click "Places" then "Connect to Server" and enter the details (protocol, ip address, username and password) of the PC whose file-system you wish to browse.

Windows has a system for Networking that finds all the other Windows PCs on the network for you automatically. Windows gives them human readable names. Linux doesn't have this. Instead, you have to tell linux the details of the other PCs and what protocol you want to use to connect to them. SSH is the normal protocol. You can also create persistent links using NFS.

There is a linux application called Samba that emulates the Windows SMB protocol and allows you to see the Windows shares and create shares that Windows will recognize. Personally, I find Samba quite tricky to configure properly. NFS is a lot easier. Using Nautilus to connect is the easiest.

---

### Post by clevertomato on 2010-08-15
drdos2006: Thanks. That link is more summarized than other howtos I've found. Still not as straightforward seeming as Windows, but I suppose that's really not apples to apples, and I can live with it (the NFS method you linked to).

yeswecan: I knew about ssh and Samba. I try to avoid Samba unless a Windows PC is involved. I use ssh plenty, but it has to be explicitly installed, and an average desktop user won't have it (the daemon) installed. Windows file sharing--at its "quickest and dirtiest" is super fast and simple with quick and easy GUI dialogs requiring just a couple clicks on each machine. Still, that doesn't mean it's best practice.

---

