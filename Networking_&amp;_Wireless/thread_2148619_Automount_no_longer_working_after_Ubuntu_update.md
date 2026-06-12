---
title: "Automount no longer working after Ubuntu update"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by MeMo_oMeM on 2013-05-26
Hi Everyone!

I use autofs to mount a remote NAS drive (running ArchLinux) using sshfs. It stopped working after the latest Ubuntu upgrade. To debug it, I started automaster with debug options (-fvd) and I am seeing:

```
attempting to mount entry /media/sshfs/crashplan
do_mount: sshfs#backup@192.168.1.200:/backup/CrashPlan /media/sshfs/crashplan type fuse options rw,allow_other,noatime using module generic
>> read: Connection reset by peer
mount(generic): failed to mount sshfs#backup@192.168.1.200:/backup/CrashPlan (type fuse) on /media/sshfs/crashplan
dev_ioctl_send_fail: token = 359
failed to mount /media/sshfs/crashplan
handle_packet: type = 3
handle_packet_missing_indirect: token 360, name crashplan, request pid 3170
dev_ioctl_send_fail: token = 360
handle_packet: type = 3
```

My system is:

```
Linux upc 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I confirmed that I have passwordless login (for all users). Unfortunately the debug messages don't tell much, and I am out of ideas. I will appreciate any suggestions!

Thanks in advance!

---

