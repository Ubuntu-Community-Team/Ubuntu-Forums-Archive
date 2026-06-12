---
title: "Sharing Files Between Two Ubuntu PCs"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by delphiexile on 2012-12-26
Hi everybody,

I'm using a switch to connect two computers running both Ubuntu 12.10 and I want to share some files between them.

How can I do this?

Thanks :)

---

### Post by bab1 on 2012-12-26
> **delphiexile said:**
> Hi everybody,

I'm using a switch to connect two computers running both Ubuntu 12.10 and I want to share some files between them.

How can I do this?

Thanks :)

You can use either [**_[COLOR="Blue"]Network File System[/COLOR]_**]("https://help.ubuntu.com/community/SettingUpNFSHowTo") (NFS) or [**_[COLOR="Blue"]Samba[/COLOR]_**]("https://help.ubuntu.com/community/Samba") (smb/cifs).

---

### Post by urielo on 2012-12-26
Hey, I have a similar issue, but I'm not using a switch. Both my laptops are coneected to a LAN via wireless, one of them is running Ubuntu 10.04 LTS (the place where files are), and the other is running Uuntu 12.04 LTS. I've tried this tutorial ([http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)) to connect via ssh, but it won't connect =//

---

### Post by Lars Noodén on 2012-12-26
If you just want to transfer some files, then OpenSSH is a lot less complicated than either NFS or Samba.  You just need to install the package openssh-server on the remote machine and connect to it with an SFTP client like Nautilus, SSHFS or plain [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html).

---

### Post by bayvista on 2012-12-29
I have 2 Ubuntu 12.04 PCs and a WD MyBookWorld NAS connected on a LAN. I can access all the NAS Shared files from my desktop, but only a few from the laptop. I am using Samba/CIFS and have setup the NAS to share all files. This is a permissions problem of some kind. I can access all files from the laptop if I use Windows. Any ideas?

SOLVED: This was caused by a different fstab entry on the laptop. These are the two entries:

Desktop://hp-nas/Public /media/hp-nas cifs auto,credentials=/home/david/.xxxxx,noexec,noperm  0  0
Laptop ://hp-nas/Public /media/hp-nas cifs iocharset=utf8,credentials=/home/pam/.xxxxx,dir_mode=0775 0   0

Changing the laptop fstab to match the Desktop gave me access to most of the missing folders. Still a few won't show.

---

