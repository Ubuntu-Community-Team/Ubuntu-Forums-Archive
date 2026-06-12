---
title: "Waiting for NFS on boot"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2009-01-22
I have a couple of NFS mounts set up in fstab. nfs-common is installed on the clients but at boot it says something about waiting for <name of mount> and the boot process is halted for a minute or so. And the mounting ends with "FAIL". After the system is up one, both or none of the NFS-mounts will be running!

I searched as best I could and found the following thread detailing what seems to be the same problem:

[http://ubuntuforums.org/showthread.php?t=620874](http://ubuntuforums.org/showthread.php?t=620874)

Now, a lot of server users must have NFS mounts set up..I would think a lot of people must have encountered this problem (bug?). Both servers and clients are running 8.10 Intrepid.

Help?

*later* This bug, I suppose? [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/275451](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/275451)

*still later*

I came up with a dirty fix for my problem. Something in the initscripts probably needs to be fixed but this will do for now:

1) Edit the NFS-mounts in /etc/fstab and put noauto as an option
2) Edit /etc/rc.local and put in lines with "mount <mountpoint>" for what you want mounted.

The NFS-server will always be up so it should be ok in my case.

---

