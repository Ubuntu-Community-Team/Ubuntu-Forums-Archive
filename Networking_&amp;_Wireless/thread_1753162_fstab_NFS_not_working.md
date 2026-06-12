---
title: "fstab NFS not working"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by njb on 2011-05-08
I just installed the 11.04 narty narwhal
I copy and past my fstab of the previous version of ubuntu and my NFS shares don't work anymore.

here is the error message :

> mount: wrong fs type, bad option, bad superblock on 192.168.1.4:/volume1/HNB,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



:( NjB :mad:

---

### Post by papibe on 2011-05-08
Is the Natty machine running as nfs server (i.e. exporting folders), or as client (i.e. mounting the shares)?

Has the server (if different) been updated also?

Could you post the result of these commands? :
```
$ dpkg -l | grep nfs

$ ls /sbin/mount.*
```

Could you also post your fstab?

Regards.

---

### Post by njb on 2011-05-09
The natty machine is NFS client
I didn't touch the server as the Natty machine has the same IP as with the previous version (10.10)

For the result of the first command
dpkg -l | grep nfs
No error and no response with this command

For the result of the second command
ls /sbin/mount.*
here is the response :
> njb@njb-REVO:~$ ls /sbin/mount.*
/sbin/mount.fuse        /sbin/mount.ntfs     /sbin/mount.ntfs-fuse
/sbin/mount.lowntfs-3g  /sbin/mount.ntfs-3g
njb@njb-REVO:~$ 


Here is my fstab file
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=84366f22-f555-495d-84e9-50f8c67b7917 none            swap    sw              0       0
# synology
192.168.1.4:/volume1/HTV	/media/HTV	nfs 	suid,dev,exec,auto,user,async,rsize=8192,wsize=8192,soft,timeo=14,intr    0    0
192.168.1.4:/volume1/HNB	/media/HNB	nfs     rw,suid,dev,exec,auto,user,async,rsize=8192,wsize=8192,soft,timeo=14,intr    0    0
#

---

### Post by njb on 2011-05-09
All of this was because Natty does not come with nfs-common installed, so if run into this problem, run synaptic and install nfs-common.

:D NjB :P

---

### Post by drazoro on 2011-05-09
> **njb said:**
> I just installed the 11.04 narty narwhal
I copy and past my fstab of the previous version of ubuntu and my NFS shares don't work anymore.

here is the error message :



:( NjB :mad:

Have you installed nfs-common ? 
$apt-get install nfs-common

---

### Post by njb on 2011-05-09
> **drazoro said:**
> Have you installed nfs-common ? 
$apt-get install nfs-common

Thank you for your answer drazoro, it came the same time as I found the solution.

See my previous post.

:popcorn: NjB :KS

---

