---
title: "Windows unable to connect to Ubuntu external HDD via Samba"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by CraigHurlington on 2013-06-08
Hello,

I have shared my Ubuntu machines /home/user/Downloads folder through samba. All Windows 7 users on the LAN are able to connect and read/write files in this directory without any user permissions issues.

I am trying to add an external hard drive to samba so that all users on the LAN will be able to use it the same way, but when connecting I am getting a 'you do not have permission to access... etc' when using Windows.

Both directory entries in /etc/samba/smb.conf are the same except the samba directory name and path.

Why am I able to connect to /Download but not /media/user/externalHDD over the network?

I have tried 'sudo chmod -R 777 /media/user/externalHDD' but that made no difference.

Any ideas or help is appreciated.

Thanks.

---

### Post by Bucky Ball on 2013-06-08
Welcome to the forums. 

What format is the external HDD? If it's EXT*, forget it. Windows won't go there. As you mention it is a 'Ubuntu' external hard drive I'm assuming this means EXT* instead of NTFS. You need NTFS.

---

### Post by CraigHurlington on 2013-06-08
> **Bucky Ball said:**
> Welcome to the forums. 

What format is the external HDD? If it's EXT*, forget it. Windows won't go there. As you mention it is a 'Ubuntu' external hard drive I'm assuming this means EXT* instead of NTFS. You need NTFS.

The External HDD is in NTFS. When I said Ubuntu HDD I was just trying to say that the HDD is infact connected to the Ubuntu machine. :)

Sorry for the confusion.

Thank you.

---

### Post by Bucky Ball on 2013-06-08
[http://ubuntuforums.org/showthread.php?t=1756575](http://ubuntuforums.org/showthread.php?t=1756575)

Solved in three posts. Or dig through here:

[http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=mount+external+drive+samba&ql=](http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=mount+external+drive+samba&ql=)

If you can't find answers in existing posts in the forum go further afield. Hope that fixes it. ;)

---

### Post by bab1 on 2013-06-08
> **Bucky Ball said:**
> Welcome to the forums. 

What format is the external HDD? If it's EXT*, forget it. Windows won't go there. As you mention it is a 'Ubuntu' external hard drive I'm assuming this means EXT* instead of NTFS. You need NTFS.

This is flat out wrong.  

I have multiple Windows clients that mount Samba shares with the underlying partition formated as EXT.  The format of the partition only matters when mounting it locally (the host machine).  When you mount the partition remotely (via Samba) the format of the file system is not important.  What is important is the *owner* and *group*. These are always set at the mount point of the client. It is a trivial task to define the user and group in the mount command or in fstab (e.g uid=1000 gid=1000 or some common group such as *users* (100) or *sambashare* (124) ).

---

### Post by Bucky Ball on 2013-06-08
Ya learn something everyday ...

---

