---
title: "Help Mounting jfs internal HD on boot"
date: 2010-04-05
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2010-04-05
I want to mount a JFS formatted drive on boot to contain my videos.

I have tryed fstab options

/dev/sda1   /home/user/mythtvvid  jfs  rw,auto,user,fmask=0111,dmask=0000   0    0

/dev/sda1   /home/user/mythtvvid  jfs  rw,auto,user,fmask=0111,dmask=0000   0    2

/dev/sda1   /home/user/mythtvvid  jfs  rw,auto,user,error=remount-ro   0    2

all of witch have failed

I could mount -t it after every reboot but would prefer to have it done automatically.  What am I doing wrong?

---

### Post by ian dobson on 2010-04-05
Hi,

Maybe try

/dev/sda1 /home/user/mythtvvid jfs rw,users,noauto,noatime 0  0

When that works try adding the extra options no after another, I've seen that if you have an error in your fstab linux doesn't mount the drive but doesn't bring any errors.

Regards
Ian Dobson

---

### Post by epi 1:10,000 on 2010-04-10
Thx for the advice.  I'm still playing around trying to find something that works.

---

### Post by ian dobson on 2010-04-10
Hi,

If your jfs partition is not your boot partition, you could just add a mount -t to your /etc/rc.local file.

Regards
Ian Dobson

---

### Post by epi 1:10,000 on 2010-04-14
> **ian dobson said:**
> Hi,

If your jfs partition is not your boot partition, you could just add a mount -t to your /etc/rc.local file.


THX.  That woked

---

