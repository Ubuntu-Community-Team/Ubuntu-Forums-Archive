---
title: "DVD/SMB Conflict"
date: 2020-09-02
forum: Multimedia Software
---

### Post by viktorsmirnov2008 on 2020-09-02
I don't know where to place this thread, so admins are more than welcome to move it elsewhere.

Basically, I attempted to setup SMB share for a DVD-mount directory. This has been done in the past, according to multiple sources.

I used SMB preexec and postexec parameters to mount/unmount the CD/DVD media, because otherwise once the media is mounted, there is nothing to unmount it. However, SMB fails to unmount the device when the connection is closed because the "target is busy". Apparently, it is busy because SMBD is using it. I attempted to bypass it by using lazy unmount.

However, I noticed that mount filesystem is stuck on whatever media was mounted first at the time of system start-up. So if I restart a computer and I insert an iso9660 media it gets mounted just fine, and then I replace the media with a UDF one, it will not be mounted. I looked into SMB logs, and it states that it basically fails to mount because of incorrect filesystem.

I use the correct CD/DVD filesystems in FSTAB, so my guess is that the issue is caused by me using a lazy unmount.

What would be the ideal way to solve this issue, so that SMB doesn't block the media from unmounting it is trying to perform?

My SMB Config:
```

[COLOR=#1C1C1C][FONT=&amp][dvd0]
[/FONT][/COLOR][COLOR=#1C1C1C][FONT=&amp]comment = External DVD
        path = /dvd0
        valid users = bobby
        create mask = 0444
        directory mask = 0555
        browseable = yes
        public = no
        locking = no
        read only = yes
        invalid users = root
        hide dot files = yes
        preexec = /bin/mount /dvd0
        postexec = /bin/umount -l /dvd0


[/FONT][/COLOR]
```

FSTAB: 
```

[COLOR=#1C1C1C][FONT=&amp]proc /proc proc defaults 0 0
/dev/sr0   /dvd0   udf,cdfs,iso9660   defaults,noauto,ro,user   0   0[/FONT][/COLOR]
```

---

