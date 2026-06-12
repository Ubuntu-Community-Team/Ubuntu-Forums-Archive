---
title: "LInux Network Shares"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by sporanox on 2008-12-03
My background is from windows server enviroment and there are many how to on smb shares, but what is the prefered way to share amongst linux client to linux server, SSH?.  I am wishing to set up a pure linux network and need a little guidance please on the direction of sharing in something other than smb.


Thanks,

---

### Post by __Ryan__ on 2008-12-03
Take a look at NFS, it is the standard for a shared file system on Linux.

Here is some documentation on it.

[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by superprash2003 on 2008-12-03
if its Linux - Linux NFS is a good option

---

### Post by timcredible on 2008-12-03
places->Home folder->right-click on any folder you want to share, choose 'share'.  if you're not admin, you may have to have that enabled for your account, system->administration->users and groups->choose user, then edit properties->user privileges, and check 'share files with local network'.

---

### Post by lswb on 2008-12-03
Nothing wrong with nfs but for quick & simple sharing on a lan it is hard to beat ssh. Just install the packages openssh-server and sshfs on the system or systems with files you want to share. No other configuration is necessary but you can use regular file permissions to restrict access as you like. Then from the gnome desktop you can just use Main Menu/Places/Connect to Server, select SSH for the server type, and enter the server name or ip address of the system with ssh-server running. your username if it is different on that system, and click connect. You will be prompted for a password and after that you'll get a folder on your desktop.

The sshfs package allows you to set up a mountpoint for the remote system and mount it similar to how you would mount a partition or filesystem on your local machine. Then you can use any file browser or command line tools to access files on the remote just as if they were on your local system.

---

