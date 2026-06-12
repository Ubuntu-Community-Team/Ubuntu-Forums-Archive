---
title: "NFS in fstab does not work"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by tzg6sa on 2012-10-06
Hi Everybody,

I've got a weird nfs problem: I can mount an nfs drive from the termnial with 
```
 sudo mount -t nfs 192.168.1.4:/media/external /media/external 
```
but I can't with fstab. My fstab looks like this: 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=3ab497bb-cec8-4bb9-9ee7-487067b39297 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=168a0ac4-3102-4d25-aa2f-09aea4417a55 none            swap    sw              0       0
# data, ntfs
/dev/sda5	/media/data	ntfs-3g	defaults	0	2
# win xp partition
/dev/sda1	/media/windows	ntfs-3g	defaults	0	2
# external nfs dirve
192.168.1.4:/media/external	/media/external	nfs	rsize=8192,wisze=8192,timeo=14,intr	0	0

```

I have installed nfs-common and portmap. I have another nfs-client machine where the nfs is working with the above fstab. Could you help me solve this issue? Any idea about what should I check is welcomed!

---

### Post by testcees on 2012-10-06
> **tzg6sa said:**
>  My fstab looks like this: 
```

192.168.1.4:/media/external	/media/external	nfs	rsize=8192,wisze=8192,timeo=14,intr	0	0

```

It is wsize= (not wisze). ;)

---

### Post by spjackson on 2012-10-06
Also, I believe you should always use the bg option for nfs mounts (unless you use noauto), because at boot time, fstab mounts occur before networking starts.

It might help if you say what errors you get from your current entry.

---

### Post by tzg6sa on 2012-10-06
Thank you!!

I have looked at the fstab entry about hundred times, but I did not spot the typo. It works now!
Also thanks for the bg suggestion!

---

