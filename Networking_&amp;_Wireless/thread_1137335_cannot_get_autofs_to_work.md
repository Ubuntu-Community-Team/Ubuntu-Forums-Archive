---
title: "cannot get autofs to work"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2009-04-25
I am unable to get autofs to work as expected.  

If I type sudo mount <ipaddr:<mount> <mountpoint> it works just fine.  but when I try to do an autofs on it, it never mounts.

heres the line in the auto.master file:
/net /etc/auto.home --timeout=600

net -rw,soft,intr,rsize=8192,wsize=8192 <ipaddress>:<mount>

then when I cd /net I expect to be able to do an ls and see the file, but they arent there.

I did an /etc/init.d/autofs reload and then an /etc/init.d/autofs restart just to be sure.

---

### Post by uniden9 on 2009-04-28
I set this up a while ago for my media pc.  I have toyed with my nfs options.

/etc/auto.master: (1 line)
/mnt /etc/auto.nfsmnt --timeout=60 --ghost

/etc/auto.nfsmnt (2 lines)
fstore_1a <nfs mount options> <ip>:<nfs mount>
fstore_1b -rw,async,nfsvers=3,hard,intr,nodev,rsize=8192,wsize=8192,noatime,user <ip>:<nfs mount>

So when its working, I should get a 
/mnt/fstore_1a  and 
/mnt/fstore_1b

I also believe I precreated the /mnt/fstore_1a and /mnt/fstore_1b
directories.   I had difficulties getting to work, but haven't messed with it since then.

Justin

---

