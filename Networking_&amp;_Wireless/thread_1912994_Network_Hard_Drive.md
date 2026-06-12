---
title: "Network Hard Drive"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by neilscaplan on 2012-01-21
I have recently upgraded to 11.10 and have lost my link to a network hard drive. When I originally set it up in 11.04 I used the following:

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

I believe I have set it all up correctly again, but when I type:

sudo mount -a

the terminal gives me a new prompt line (i.e. no error message) but the drive doesn't appear on my desktop.

Can anyone suggest a solution?

I should also add that when I type "mount" to see what is mounted I get the following:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/neil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neil)
//192.168.1.67/Public on /media/public type cifs (rw)
//192.168.1.67/Public on /media/Public type cifs (rw)
//192.168.1.67/public on /media/public type cifs (rw)

The supposed mounted drive is there three times at the bottom (because I have attemped to mount it three times!).

Any help would be really useful as I really don't know how to fix this...

---

