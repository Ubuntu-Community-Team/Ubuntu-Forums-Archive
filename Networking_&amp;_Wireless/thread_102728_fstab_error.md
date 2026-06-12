---
title: "fstab error"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by jbraum on 2005-12-12
I trying to mount a smb share with a username and passwd but I'm getting the following error.

[mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/Braumbergers in /etc/fstab or /etc/mtab

Here's my fstabconfig

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /boot           ext3    defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//Lily/Braumbergers     /media/Braumbergers  smbfs   auto,username=xxxxxxx,password=xxxxxx,uid=your username 0 0

---

### Post by mlomker on 2005-12-12
I assume you created the directory?  I personally prefer to use mount commands instead of fstab for smb...just add it at the end of /etc/init.d/bootmisc.sh

Your options aren't correct, though.  [Look here.]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")

---

### Post by jbraum on 2005-12-13
I'm see the mount but it's not mounting.  I'm getting the following error.

mount: only root can mount //linux_julie/Braumbergers on /media/Braumbergers

I have the following entry:

//linux_julie/Braumbergers	/media/Braumbergers	smbfs	auto,username=username,password=password,uid=username 0	0

Of course the username is the actual user for the share.

---

### Post by taurus on 2005-12-13
Instead of trying to mount it thru /etc/fstab, see if you can mount it from a command line first!!!

---

### Post by jbraum on 2005-12-14
Ok here's what I've tried:

I followed the how to on [unbuntuguide.org]("http://www.ubuntuguide.org/#automountnetworkfoldersall")

That setup a share in /media/dino that's ok.  But nothing mounted.  I did the following command to mount the share.

sudo mount //linux_219/dino /media/dino/ -o username=dino,password=33333,dmask=777,fmask=777

 ...and get

mount: wrong fs type, bad option, bad superblock on //linux_219/dino,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Checked the syslog

Dec 14 09:31:21 localhost kernel: [4296288.734000] smbfs: mount_data version 1919251317 is not supported

I am able to access the file when I connect to the server

smb://SIMP%3B@linux_219/dino
prompts the correct username and password and I'm in.

I just want to be able to mount the share.  Any help would be grateful

Jeff

---

### Post by mlomker on 2005-12-14
[QUOTE=jbraum]
mount: wrong fs type, bad option, bad superblock on //linux_219/dino,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/QUOTE]

You've installed the **smbfs** package?  I think I saw that error once when it wasn't installed.

---

### Post by hod139 on 2005-12-14
As mlomker just stated, make sure you have the smbfs package installed, and then try 
```

sudo mount -t smbfs //linux_219/dino /media/dino/ -o username=dino,dmask=777,fmask=777

```
You need to specify the -t option to tell mount the filesystem type.  You don't need to give your password, it will prompt.

---

### Post by jbraum on 2005-12-14
[QUOTE=mlomker]You've installed the **smbfs** package?  I think I saw that error once when it wasn't installed.[/QUOTE]

That was it - install smbfs -  Installed and mounted.

One other if I have multiple random (say 20) users using the computer at different times.  Is there away that each users share could mount on login?  Or better yet have each user login as guest but all shares mount (perferably not on the desktop) so that each user could double click his share and login to it.  I'm a teacher in a 6th-8th grade, that has many users and I'm trying Linux in the lab and need to make it as easy as possible.

Thanks for the help

---

### Post by xeo_pt on 2005-12-18
Wrong threat!

---

