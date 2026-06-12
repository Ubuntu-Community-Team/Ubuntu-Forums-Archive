---
title: "Nautilus crashes while browsing share via CIFS"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by rubenverweij on 2008-12-21
Hello everyone,

I followed [this]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") guide to mount my Iomega external ethernet harddisk. That works fine, it successfully mounts the drive on startup. However, when I try to browse it, Nautilus crashes after +- 30 seconds. The files are correctly listed before the crash. This is my fstab line:
```
//192.168.1.20/User  /media/iomega  cifs  uid=1000,gid=1000,credentials=/home/user/.smbcredentials,dir_mode=0777,file_mode=0777  0  0
```
This is the output of dmesg | grep -i cifs:
```
user@ubuntu:~$ dmesg | grep -i cifs
[  137.360077]  CIFS VFS: server not responding
[  137.360098]  CIFS VFS: No response for cmd 50 mid 123
[  182.360093]  CIFS VFS: server not responding
[  182.360114]  CIFS VFS: No response for cmd 50 mid 320

```
I am able to connect to the drive via FTP.
I hope someone knows a solution for this problem!
Thanks in advance,
Ruben Verweij

---

