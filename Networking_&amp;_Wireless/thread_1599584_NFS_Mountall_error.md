---
title: "NFS Mountall error"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by bertmanphx on 2010-10-18
Hello,
I have an NFS error that has been going on for quite some time.  Upon boot, I get a mountall error that it cannot mount the two shares below.  If it follow the "M" prompt, and issue the mountall --force-fsck command, I can finish the boot sequence and log in.  II have two directories exported on my server running 10.04.  They are listed below:

/media/raid 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
/media/music 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)

I can only mount these successfully if I wait until the client is booted, then mount them manually.  I get what appears to be the same error with 10.04, 10.10, and Kubuntu 10.04 as clients.  Strangely, Fedora 13 mounts both just fine.

I am mounting them in fstab as:
192.168.0.71:/media/raid /home/robert/titan

Any ideas?

Thanks,

bertmanphx

---

