---
title: "Auto mount windows network drive"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by adsf on 2009-01-18
Hi guys, 

Trying to auto mount a windows drive so I can clamscan and grsync to easy.  

I have created a

/media/server

then tried addig to fstab

//10.1.1.10/c  	/media/server  	auto  	ro,noauto,user,exec  	0 0

i am using 8.10 any help would be appreciated.

Thanks in advance

---

### Post by Whizam on 2009-01-18
I used Smbafs to do this.

```
sudo apt-get install smbfs
```

Add this into your /etc/fstab to make it permanent:

```
//[server name or ip]/[share name] [directory to mount share into] smbfs username=[samba username],password=[samba password] 0 0
```

For a non-permanent solution, run this command:

```
mount -t smbfs //[server ip or domain name]/[server directory] [place that you want to mount the directory] -o username=[samba username],password=[samba password]
```

I made a quick _[Post]("http://www.jonhoweonline.com/linux/how_to_mount_a_samba_share_to_your_computer_in_linux/")_ on it a while ago with more info:

---

### Post by reidi on 2009-01-19
I've set up fstab so my ubuntu 8.10 box automatically mounts a share on a separate WIndows XP Home machine.  No problem there.  grsync can operate just fine updating the contents of subfolders below the root level of the share.

The problem is that grsync cannot create directories on the root of that share. Here is what fstab looks like:

//windows_box/share /mnt/photos cifs credentials=/path/to/creds,exec,rw 0 0


I have tried many different variations of dir_mod and file_mod and umask parameters, but when the share is mounted, an ls -l in /mnt shows something like:

dr-xr-xr-x photos  blah blah

Doesn't matter what /mnt/photos is before the mount (drwxrwxrwx), it gets changed to the above perms when mounted.

So, can the share be mounted so I can create folders at the root level of the share, e.g. photos/new_folder ?

---

### Post by Iowan on 2009-01-19
[This]("http://ubuntuforums.org/showthread.php?t=288534") How-To provides a wealth of Samba information - mounting in particular.

---

