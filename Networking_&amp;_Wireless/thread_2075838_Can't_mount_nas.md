---
title: "Can't mount nas"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by xendistar on 2012-10-24
I am trying to mount my nas via the fstab file, I have added the following line to my fstab file

//192.168.0.57/openshare/data /media/share cifs credentials=/root/.smb 0        0

But when I try the command sudo mount -a

I get the follwoing error

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

the  .smb file contains my username and user password. I have tired to  making my credential file a simple .txt file but that made no difference
 
I  had a similar in my fstab file under Debian and Debian Mint but due to  my own stupidity I lost the partition (don't ask :( ) so I am unable to  replicate it

---

### Post by TheFu on 2012-10-24
Does [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) help?

---

### Post by xendistar on 2012-10-25
OK, I tried the

//192.168.0.57/openshare/data /media/share cifs credentials=/home/[I]
myusername[/I]/.smb,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0  but I got a variety of errors like

mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

In the end I found an old copy of my fstab file and used the following

//192.168.0.57/openshare/data /media/share cifs defaults,uid=*myusername*,gid=users 0    0

This allows me to mount the nas have read write access to the it but only allows other users on my network read access to the nas 

Is there anything I can do to allow users read right access to the nas?

---

### Post by TheFu on 2012-10-25
I don't know, but I'd start by reading the man page for the mount.cifs command like the error message suggests and look for dynamic user/group permissions.  

What are the file and directory permissions set to be?  If they are NTFS, then using a Windows PC may be easier to see them and control them.  Last time I checked, NTFS permissions behaved differently depending on if you were locally on the machine or coming in over a network share. Over the network was more restrictive on the file permissions.

The other option would be to use UNIX/Linux-based file systems on your NAS, not Windows. Then you could use NFS and have complete user/group file permissions management under Ubuntu.  The permissions would be the same whether local or NFS mounted.  This isn't always possible with every NAS device.

My cheap NAS doesn't enforce any file/directory permissions on NTFS drives. OTOH, the expensive NAS presents iSCSI LUNs, so block devices are available for any OS to control. 

Over the years, I've learned to always use storage in a native UNIX/Linux file system. It can be presented to client machines of any type that way, samba, NFS, AFS, whatever;  while retaining the underlying superior capabilities and flexibility of Linux file system management.  With a Windows-based solution, we are stuck with NTFS management and permissions.  You may not have that option. It all depends on the NAS capabilities.

I wish I had a better answer. Sorry.

---

### Post by xendistar on 2012-10-27
Well I have resolved it, I used the instructions from this post on here

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

The first post gave me all the info I needed, added wins and winbind as instructed and I am up and running.

---

