---
title: "Cannot mount network share after static dhcp change"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by Shazzner on 2010-01-16
I've got an NAS box that I hold all my files in.
I went through this process:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Which worked great and basically had a mapped network drive. Unfortunately when I changed my router to assign a static ip to my NAS it stopped mounting.

I double checked my fstab config it has this:
```
//dlink-6402c4/volume_1/files /media/dlinkfiles cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```
However I get this when I try to remount it:
```
$ sudo mount -a
mount error: could not resolve address for dlink-6402c4: No address associated with hostname
No ip address specified and hostname not found
```
What am I missing here? I haven't actually tried to remove the static dhcp but doing so seems a little silly...

Edit: I just want to mention I can access it just fine by doing the old route of Places -> Network; I just can't mount it.

---

### Post by byStanderone on 2010-01-16
...perhaps you have to update your fstab file, take the correct uuid from 

 'sudo blkid'  then edit your fstab file.

---

### Post by Shazzner on 2010-01-16
hmmm I'm just getting local drives; my ext3 and swap partitions.

E: Adding the UID of my local drive netted nothing...

---

