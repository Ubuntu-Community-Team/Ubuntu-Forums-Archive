---
title: "Mounting samba share via mount.cifs"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by jc0028 on 2010-02-07
Hi, my first post to this forum!

I have Ubuntu 9.10 running, trying to mount an Iomega Network Hard Drive (NAS) called "bigboy" which makes available a share \\bigboy\public.  Any username and a blank password will log into the share.

I can access it from various users via:
smbclient //bigboy/public hitting <enter> for the blank password

And from windows I can see all the files too.

But, if I mount the share using CIFS (either via an entry in /etc/fstab or via the command line) then the share will mount, but I won't see any files in it e.g.

mount.cifs //10.0.0.254/public  /media/iomega -o username=root,password=,rw

I am guessing this is something to do with the Iomega drive using LANMAN security  (because I get a message to that effect when I try other combinations of command parameters in smbclient) but I tried turning on client lanman auth=yes in the samba config file and its still showing no files.

By the way if anyone knows how to set the client debug level when using mount.cifs that might also be helpful as it seems the old smbmount / mount.smbfs had a debug level you could set (which is now disabled due to deprecation) and helpfully the new CIFS doesnt have any options for debug level.

Any ideas?  Thanks!

---

### Post by Iowan on 2010-02-07
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To?

---

### Post by jc0028 on 2010-02-07
Brilliant, there it is:

**KARMIC: Files owned by root / "The folder contents could not be displayed"**
Note for KARMIC users encountering this error:
There is a bug affecting some users (particularly those with NAS devices like the Timecapsule) which gives the same symptoms as this problem. Bug report is here: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/406466]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406466")

Fix is simple, just add the "noserverino" option to the mount command like so:

Thank you so much!

---

