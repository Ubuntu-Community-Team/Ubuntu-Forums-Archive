---
title: "Can't create permanent windows share mount"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Stolea on 2010-05-01
I have been successfully creating permanent windows share mounts on Ubuntu since v8.04 by following the instructions in 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")
My fstab file has this line
```
//192.168.0.2/office_d  /media/office_d  cifs  credentials=/home/peter/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
```
which in the past has mounted the windows share without any problems.
For some reason this doesn't work anymore. The .smbcredentials file is in the same place it has been since it was created. I have verified that .smbcredentils is in the correct place.
In order to find out what the problem might be, I tried 
```
dmesg | tail
``` 
and got the following response
> [   18.428245] type=1503 audit(1272697118.037:15):  operation="capable" pid=1249 parent=1245 profile="/usr/sbin/cupsd" name="sys_admin"
[   18.432914] usb 1-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   19.516273]  CIFS VFS: No username specified
[   19.516278]  CIFS VFS: cifs_mount failed w/return code = -22
[   20.465725]  CIFS VFS: No username specified
[   20.465730]  CIFS VFS: cifs_mount failed w/return code = -22
[   21.602779] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   27.820011] eth0: no IPv6 routers present
[  108.894261]  CIFS VFS: No username specified
[  108.894265]  CIFS VFS: cifs_mount failed w/return code = -22
peter@Shop:~$ sudo mount /media/office_d
mount: wrong fs type, bad option, bad superblock on //192.168.0.2/office_d,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can't pretend that I understand the full message, but it seems to say that it can't find/read the .smbcredentials file and as a result can't mount the share.
When I change the code to
```
192.168.0.2/office_d  /media/office_d  cifs  username=xxxx,password=xxxx  0  0
```
where xxxx is my username and password, the share mounts without any problems.
I can't work out what I am doing wrong. Has the code changed? For obvious security reasons I don't want to place the username and password in the fstab file where everyone can see it. Any help welcome.

---

### Post by LasloHollyfeld on 2010-05-02
> **Stolea said:**
> I have been successfully creating permanent windows share mounts on Ubuntu since v8.04 by following the instructions in 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

...
> **Stolea said:**
> 
I can't work out what I am doing wrong. Has the code changed? For obvious security reasons I don't want to place the username and password in the fstab file where everyone can see it. Any help welcome.
Try "sudo apt-get install smbfs". I had the same problem, and I'm suspecting that the standard mount command can only handle simple stuff, and you need mount.cifs (which is in the smbfs package) to handle the special "credientials=" parameter.

---

### Post by Iowan on 2010-05-02
[Here]("http://ubuntuforums.org/showthread.php?t=1186877") is another option to consider...

---

