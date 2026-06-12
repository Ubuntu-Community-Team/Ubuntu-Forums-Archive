---
title: "I cant get nfs working"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by hawkish on 2010-10-24
I am trying to share two folders on my linux NAS drive with my minimal ubuntu linux install of xbmc but so far failing.
 
On the NAS I intend to share
  ```

  /home/Public/eDownloader/TV
 /home/Public/eDownloader/movies 
```
I have edited the Exports file to:-
 
  ```

 /home/Public/eDownloader/movies 192.168.1.111(rw,no_wdelay,sync,insecure,no_root_squash,no_all_squash,no_subtree_check,insecure_locks,no_acl)
/External 192.168.1.111(rw,sync,no_wdelay,insecure,no_root_squash,no_all_squash,no_subtree_check,insecure_locks,no_acl)
/home/Public 192.168.1.116(rw,wdelay,sync,insecure,no_root_squash,no_all_squash,no_subtree_check,insecure_locks,no_acl)
/External 192.168.1.116(rw,wdelay,sync,insecure,no_root_squash,no_all_squash,no_subtree_check,insecure_locks,no_acl)
/home/Public/eDownloader/TV 192.168.1.111(rw,no_root_squash,async) 
and I want these to be available to XBMC in a folder called "NFS" located here  Code:
 /home/xbmc/NFS 
```
I have edited the fstab folder on the xbmc machine to the following
  ```

 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
#      
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b58e6491-be02-4e0b-b6f4-525f408cfc3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3d95532-5bf9-44ff-8b3c-d263815cad4d none            swap    sw              0       0
### NFS shares ###
192.168.1.127:8080/home/Public/eDownloader/TV      /home/xbmc/NFS     nfs     rsize=8192,wsize=8192,timeo=14,intr
192.168.1.127:8080/home/Public/eDownloader/movies      /home/xbmc/NFS     nfs     rsize=8192,wsize=8192,timeo=14,intr 
```
Can anyone see what ive done wrong. I have rebooted both machines a couple of times and had no luck
 
Thanks in advance

---

### Post by luvshines on 2010-10-24
Though I am not sure, but I think the 8080 is wrong. Did you do anything on NFS server for it to be available on 8080 port ??

Also, I don't think you will be able to mount both the shares on the same directory.
I either mount them on two different directory under same parent directory or mount bind on the server side itself (if that is useful to you)

---

### Post by Jose Catre-Vandis on 2010-10-24
Read the [howto]("http://ubuntuforums.org/showthread.php?t=249889") (If you are using lucid as your NAS, watch out for version requirements (read the last few posts on the howtofor help with this)

Just work on one share to start with, once you have that working, add more using the same principles

"luvshines" is right, you will need to mount each share in a separate directory, for example:

Share:   /home/Public/eDownloader/TV      
Mount:   /home/xbmc/NFS/TV

---

### Post by hawkish on 2010-10-24
fantastic advice, thank you both very much. As stated the port 8080 was not needed and seperate client folders were needed. Thanks again I will try and help out where I can:KS

---

