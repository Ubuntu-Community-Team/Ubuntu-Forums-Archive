---
title: "Mounting Cifs share with certain options results in empty mount"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by Garibaldi3489 on 2012-08-01
Hello,

I am running Ubuntu 12.04 64-bit server on a fileserver and Ubuntu 12.04 64-bit desktop on my local machine. I have configured Samba on the server with two shares as follows:
```
 
[Share1]
   path = /mnt/Share1
   browseable = yes
   public = yes
   guest ok = yes
   writable = yes
   printable = no
   create mode = 0664
   directory mode = 0775
   veto oplock files = /*mgc*/
[Share2]
   path = /mnt/Share2
   browseable = yes
   public = yes
   guest ok = yes
   writable = yes
   printable = no
   create mode = 0664
   directory mode = 0775
   veto oplock files = /*mgc*/

```
I have also configured two virtual IP addresses, 192.168.1.2 (on eth0:0) and 192.168.1.3 (on eth0:1) so that I can access Share1 via \\192.168.1.2\Share1 and Share2 via \\192.168.1.3 for compatibility with how shares were configured on the previous hardware. I can mount Share1 over CIFS without a problem, however if I try to mount Share2 with any mount options besides username and password, it completes successfully (return code is 0) but the mount point is blank:
```
# mount -o username=user,password=pass,nounix //192.168.1.3/Share2 /mnt/tmp ; echo $?
0
# ls /mnt/tmp
# grep /mnt/tmp /etc/mtab
//192.168.1.3/Share2 on /mnt/tmp type cifs (rw)
# umount /mnt/tmp
# echo "now I'll try it without the nounix option"
now I'll try it without the nounix option
# mount -o username=user,password=pass //192.168.1.3/Share2 /mnt/tmp ; echo $?
0
# ls /mnt/tmp
file1 file2 file3
# grep /mnt/tmp /etc/mtab
//192.168.1.3/Share2 on /mnt/tmp type cifs (rw)
```

Trying to access Share2 via 192.168.1.2 results in the same behavior. The permissions on the share directories on the server are the same:
```
drwxr-xr-x 243 root root 4096 Jul 11 23:01 Share1
drwxr-xr-x  30 root root 4096 Jul 31 20:36 Share2

```

Any ideas on what is causing this share to be inaccessible?

---

