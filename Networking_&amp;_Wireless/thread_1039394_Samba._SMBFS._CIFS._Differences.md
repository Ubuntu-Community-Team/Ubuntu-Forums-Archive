---
title: "Samba. SMBFS. CIFS. Differences?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-01-14
I run Samba at home because I use linux, osx, xp and vista on several different computers. I use one central ubuntu machine as my "server" which houses all of my data, which obviously also has the samba accounts set up.

I read that smbfs hasn't been maintained in a couple years and the focus was shifted to cifs. What exactly is that? If I'm running Samba at home, am I basically running an ancient protocol since it hasn't been maintained in years? Or is Samba different from SMBFS itself?

My setup:

I simply installed samba, edited the smb.conf file, added accounts, set permissions to those accounts to my network drive inside my Ubuntu computer, and restarted the Samba daemon.

Am I running "SMBFS?"

---

### Post by albinootje on 2009-01-14
> **Roasted said:**
> 
Am I running "SMBFS?"

This page :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
is a little unclear about why you would want to install the smbfs package.

But I think that if you didn't install the package smbfs, and you're not using smbfs in any of your mount commands, then you're not using smbfs.

I'm using autofs + samba since years at work.
I still need to check whether "smbfs" or "cifs" is used in the relevant autofs config file.

---

### Post by Roasted on 2009-01-14
I used the command "blkid" to find the actual ID of each hard drive.

Then I added those drives to my fstab file. My drives auto-mount when I start up my Ubuntu computer to a designated directory I created in /media. Then, I set up Samba to look at the directory in question.

I never issue a mount command. Fstab (thanks to blkid) take care of that for me.

---

### Post by Iowan on 2009-01-14
> **Roasted said:**
>  Or is Samba different from SMBFS itself? Yes, Samba is different from smbfs.  In fact, if you install the **smbfs **package, you actually get **cifs ** (if I remember other threads correctly).  There IS a difference in the mounting technique between the two. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a **cifs** How-To.

---

### Post by Roasted on 2009-01-14
So more or less, I'm not using SMBFS OR CIFS?

---

### Post by Iowan on 2009-01-14
If your Samba server is working, I *suspect* you're using one or the other... > I never issue a mount command. Fstab (thanks to blkid) take care of that for me. What's in /etc/fstab?

---

### Post by albinootje on 2009-01-14
> **Iowan said:**
> If your Samba server is working, I *suspect* you're using one or the other...  What's in /etc/fstab?

I thought I read some time ago about the Samba project that the name of the protocol SMB was gonna change to CIFS.

[http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block)
[http://de3.samba.org/samba/devel/#learn](http://de3.samba.org/samba/devel/#learn)

Binaries from the smbfs package :
```

$ dpkg -L smbfs
--> binaries only :
/sbin/mount.smbfs
/sbin/mount.cifs
/sbin/umount.cifs
/usr/sbin/cifs.upcall
/usr/bin/smbumount
/usr/bin/smbmount

```

After removing (purging) smbfs I could still successfully do this :
```

mount -t cifs //192.168.44.44/test44 /mnt -o username=guest,password=ubuntu

```

And that means it should work from /etc/fstab too.

---

### Post by Roasted on 2009-01-15
Well, out of curiosity I uninstalled SMBFS and on my iBook G4 with OSX 10.4 installed I was able to connect to smb://jason-intrepid without any issues.

So I assume I am not using SMBFS to mount my shares. I mean, after all, the shares are mounted automatically through fstab when I boot up. I also just put in an SD card and used "umount" to unmount it. I was reading that "mount" is often SMBFS. Is it? What's the scoop on that? Isn't mount an actual linux command, along with umount?

As requested, my fstab and blkid.

BLKID
```
jason@jason-intrepid:~$ blkid
/dev/sda1: UUID="74DA6CA11CE45FF4" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="10b66b98-07bc-4b41-acc5-3f12c86d1d9a" 
/dev/sda3: UUID="ab1ec851-8bb9-4a63-b045-ba7e2fc4b444" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda4: UUID="e94a403e-832a-45c3-b3ae-b1b19025c945" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="b2354e40-cd24-41eb-b41b-0aadc9933166" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="10b66b98-07bc-4b41-acc5-3f12c86d1d9a" 
/dev/sdb3: UUID="ab1ec851-8bb9-4a63-b045-ba7e2fc4b444" TYPE="ext3" 
/dev/sdb4: UUID="e94a403e-832a-45c3-b3ae-b1b19025c945" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="772764b7-e571-4897-ba6d-ded412a5e814" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="b862f78f-4fcc-4d41-9d64-b7534da2dc84" SEC_TYPE="ext2" TYPE="ext3" 
```

Fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                 proc         defaults                    0  0  
# /dev/sda3
UUID=ab1ec851-8bb9-4a63-b045-ba7e2fc4b444  /                     ext3         relatime,errors=remount-ro  0  1  
# /dev/sda4
UUID=e94a403e-832a-45c3-b3ae-b1b19025c945  /home                 ext3         relatime                    0  2  
# /dev/sda2
UUID=10b66b98-07bc-4b41-acc5-3f12c86d1d9a  none                  swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0         udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1         udf,iso9660  user,noauto,exec,utf8       0  0  

#/dev/sdb1 
UUID=b2354e40-cd24-41eb-b41b-0aadc9933166  /media/localbackup    ext3         defaults                    0  0 

#/dev/sdc1 
UUID=772764b7-e571-4897-ba6d-ded412a5e814  /media/storage        ext3         defaults                    0  0  

#/dev/sdd1 
UUID=b862f78f-4fcc-4d41-9d64-b7534da2dc84  /media/storagebackup  ext3         defaults                    0  0  
```

sdb1 = localbackup. An rsync'ed copy of my main drives home directory.
sdc1 = storage. Network drive for Samba. Houses the Samba user shares.
sdd1 = storagebackup. Simply a backup drive for sdc1.

I have 4 drives.
Two sets.
Of those sets, two main (My main + network main) and two backup (main backup and network backup).

---

