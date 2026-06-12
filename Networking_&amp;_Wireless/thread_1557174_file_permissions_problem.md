---
title: "file permissions problem"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by walter_j on 2010-08-20
I have directories on a ubuntu server that i want everyone to have permission to rwx as follows:

walter@ubuntu-srvr:/home/public$ ls -l
total 12
drwxrwxrwx  2 nobody nogroup 4096 2010-07-24 23:10 Downloads

On my desktop, i mounted the share with the following in fstab:
//192.168.1.99/public /mnt/srvr cifs credentials=/etc/smbpasswd,defaults,rw 0 0

when i list the mounted share the permissions are root:
walter@walter-ubuntu:~$ ls /mnt/srvr -l
total 0
drwxr-xr-x 1 root root 0 2010-07-24 23:10 Downloads


what am i doing wrong?

---

### Post by nulldozer on 2010-08-20
I imagine this is not the best solution, but if you just want to be able to access and edit your files when you mount the share, try
```
//192.168.1.99/public /mnt/srvr cifs credentials=/etc/smbpasswd,defaults,rw,**noperm** 0 0
```

---

### Post by walter_j on 2010-09-07
I added noperm,file_mode=0777,dir_mode=0777 but ls still shows the share as owned by root. When i try to backup pictures I still get permission errors.

---

