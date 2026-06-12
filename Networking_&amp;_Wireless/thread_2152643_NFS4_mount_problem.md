---
title: "NFS4 mount problem"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by devaj on 2013-06-08
Hi,
I have been experimenting with nfs4.I am facing a dilemma with nfs4.I want the nfs-client to only see a particular sub-directory not the whole directory structure when mounting the export.For example I would like the client to see only the home directory instead of whole subdirectory structure inside netboot which is acting as the root export.Using the hide option does not work.Here's the /etc/exports sample.

```
/netboot     10.0.2.0/24(ro,async,root_squash,no_subtree_check,hide)
/netboot/home    10.0.2.87(rw,sync,root_squash,subtree_check,no_hide)
```

I would appreciate if someone could help me out.
I really hope that this question does not go unnoticed unlike the the question posted by a humble fellow on this forum [http://ubuntuforums.org/showthread.php?t=1603881](http://ubuntuforums.org/showthread.php?t=1603881).
I really hope some one would answer this question and put a stop to this kind of question being asked again and again.

---

### Post by LewisTM on 2013-06-10
Hi there!

First off, this page is a good place to start when setting up NFSv4
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

Basically, NFSv4 lets your setup the server directory structure the way you want it. Its full potential is unleashed with **bind mounts**.

So first create an NFS home, e.g. /nfs, and empty subdirectories e.g. /nfs/home
Then set the machine to mount a instance of /netboot/home inside /nfs. In /etc/fstab, add the entry
> /netboot/home /nfs/home   none    bind  0  0

Your /etc/exports should look like this:
> /nfs   10.0.2.0/24(ro,async,no_subtree_check,fsid=0)
/nfs/home    10.0.2.87(rw,sync,subtree_check,nohide)
[FONT=Courier New]root_squash [/FONT]is implicit.
Reboot. Your clients should be able to mount with an fstab entry along those line:
> <serverIP>:/home <localdir> nfs <mountparameters> 0 0

Cheers!

---

