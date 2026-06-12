---
title: "Can not share NTFS part"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by sedat21 on 2012-01-27
Hi

I use Ubuntu 11.10 and Windows 7 on all machines on my local network.

The file sharing is properly between Windows-Windows. Also I can see from Ubuntu the files which are shared by Windows. I can use them and I can edit them. Also when I share from Ubuntu files which are stored on EXT file system, I can use them properly from other machines. Everything is good until here.

But when I share files which are stored on NTFS part, I can see that this folder is sharing by Ubuntu but I can not access them from other machines. I can even not access them on the same machine (which runs Ubuntu) from Nautilus --> "Browse Network". I get this error when I want to access these from Windows

---
Network error
Windows, \\sedat21\testfolder could not access the path
Check the file name. If it is true, that means there is a problems about your network.
Error code: 0x80070035
Could not found path from network.
---
(Note: I translate the error to English.)

When I try to access the files from the same machine which runs Ubuntu, I get this error:

---
Unable to mount location
Failed to mount Windows share
---

Can somebody can help me to understand why I can share EXT files properly but not NTFS files :(

Thank you!

---

### Post by rcayea on 2012-01-27
Quick question that might help me or others help you?

Do you have Samba installed?

---

### Post by sedat21 on 2012-01-27
@rcayea On Ubuntu 11.10 Nautilus when you want to share, It asks to install Samba. So yes I installed.

---

### Post by rcayea on 2012-01-27
Have you then configured the smb.conf file?

Do you have system-config-samba?

I found that little gem to be a helpful program.

And to be sure, you did set your Windows machines as visible and share-able?

---

### Post by sedat21 on 2012-01-27
I have not configured anything onsmb.conf file. (Everything is default not after format Ubuntu.)

system-config-samba is installed on Ubuntu. I diD not installed it manually, I think it is installed automatically when I installed Samba.

I can share from Ubuntu any file which are stored on EXT file system. But if the files are on NTFS part, I can not access them from any machine (even the same machine which run Ubuntu).

---

### Post by rcayea on 2012-01-27
Have you looked into your authentication software?

---

### Post by sedat21 on 2012-01-27
> **rcayea said:**
> Have you looked into your authentication software?

What do you mean exactly?

---

### Post by sedat21 on 2012-01-27
How can (with which command) i mount an NTFS partition with full access and write permissions to everyone (quest, anonym users from network... all)?

---

### Post by rcayea on 2012-01-27
Not ignoring you...just busy at my job will reply when i can .

---

### Post by rcayea on 2012-01-27
This from the Gentoo website might help:
[http://en.gentoo-wiki.com/wiki/Mounting_Windows_Partitions](http://en.gentoo-wiki.com/wiki/Mounting_Windows_Partitions)

and this from teh arch wiki:

[https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)

---

### Post by sedat21 on 2012-01-27
> **rcayea said:**
> This from the Gentoo website might help:
[http://en.gentoo-wiki.com/wiki/Mounting_Windows_Partitions](http://en.gentoo-wiki.com/wiki/Mounting_Windows_Partitions)

and this from teh arch wiki:

[https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)

Actually I could not mount the NTFS for all user or I don't know if the Nautilus does this thing already...

---

### Post by sedat21 on 2012-01-28
Can somebody help me please?! :(

---

### Post by Morbius1 on 2012-01-28
If you are mounting the NTFS partition from Nautilus instead of through fstab then it will mount with you as owner and access limited to you alone. You have 2 options at this point:

[1] Make all samba clients appear to be you:

* Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```* Add the following line to the [global] section of smb.conf - right under the "workgroup" line:
```
force user = your-linux-user-name
```* Save smb.conf and restart samba:
```
sudo service smbd restart
```[2] Add an entry to your fstab file to automount this NTFS partition with permissions consistent with remote access. Something like this:

```
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```To find the correct UUID number run this command:
```
sudo blkid -c /dev/null
```And don't forget to create the mount point: 
```
sudo mkdir /media/WinD
```[COLOR=Blue]Note[/COLOR]: I do not recommend mounting the Windows OS partition in write mode and certainly don't recommend sharing it across the lan in write mode but that decision is yours.

---

### Post by sedat21 on 2012-01-28
@Morbius1 first thank you! After mounting the part and share it with others (as root using nautilus) it worked. But i need to ask simple questions to understand what is going on. I will be happy if you can answer them too.

1) I don't wanna use fstab file. With which command i can mount the NTFS part to do the same thing with this:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,windows_names 0 0

2) Why we add this line to samba config file:
force user = your-linux-user-name

3) Why you don't recommend to mounting (or sharing) the Windows OS NTFS file.

Thank you again :)

---

### Post by Morbius1 on 2012-01-28
By default when you mount an NTFS partition in Nautilus it mounts with you as owner and permissions of 0700 or drwx------. That means only you have access and no one else. 

If you created a samba share on your system that allows guest access or access by a specific user then the remote user is not you so although you told samba to allow others access, nothing can override Linux permissions other than root.

If you don't want to use fstab then you can use the "force user" option in smb.conf.  The remote user, after providing authentication if that is how you set these shares up or as a guest, will be converted to you for these shares. Now the remote user has access to the share.

As for not allowing write access to the WindowsOS partition - I guess I'm just old school about this sort of thing. There's just to big a risk that something will go wrong. Share an NTFS "data" partition and having something goes wrong is one thing. But who wants to reinstall Windows if you share it's partition?

---

### Post by sedat21 on 2012-01-28
Morbius1 and rcayea Thank you so much. It works now perfect.

---

