---
title: "Can I import music to exail from a external hdd shared with smb?"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by -GC- on 2007-09-17
Hey yall
I finally got Exaile to run and so far it's awesome, but i have one problem..
How can i import my music that is on an external hard drive shared with smb?
I would appreciate any idea's :)

---

### Post by veloce on 2007-10-01
If you haven't resolved this already:

Exaile needs the drive to appear local.  The way to do this is to mount the smb file system rather than access it "remotely".

1 Check that smbfs is installed
```
sudo apt-get install smbfs
```
2 Use the command 
```
gksudo gedit /etc/fstab
```
to add the following line to fstab for the mount:
```
//windowscomputer/smbshare /mnt/Music cifs defaults,credentials=/root/.sambapassword 0 0
```
3 Use the command
```
gksudo gedit /root/.sambapassword
```
To create a file for the username and password for the share.  The file should contain the lines:
```
username=smbusername
password=smbusername'spassword
```
4 create the directory that it will be mounted to (as in the line in fstab):
```
sudo mkdir /mnt/Music
```
5 mount the share manually (on reboot it will happen automagically).
```
sudo mount /mnt/Music
```

---

### Post by kjpmcgee on 2008-01-02
I am new to Ubuntu and trying to get the same thing to work in Exaile. I tried the above suggestion, but I keep getting an error: 

can not find /mnt/Music in /etc/fstab/ or /etc/mtab

:confused:

Any help would be appreciated. Thanks.

---

