---
title: "mksquashfs consistenly hangs at 92%"
date: 2008-08-04
forum: Mythbuntu
---

### Post by dannysauer on 2008-08-04
So, the image was initially created fine by ltsp-build-image.  I booted from it, everything was grand.  I then added the ldap client auth stuff, added a couple of NFS mounts to the fstab, and modified a couple of UIDs and GIDs within the chroot to match ldap.  I also removed /var/cache/apt/archives in the chroot since that's NFS mounted on the client.  Now, when I run ltsp-update-image (with no args), mksquashfs gets to 92% and hangs there.  It's been there for almost 24 hours now, so it's not just my impatience. :)

Is there a way to turn up the verbosity so I can see what's happening?  Is this something expected?  I'd blame the removal of apt-cache, but mksquashfs just bundles the folder up without regard to what the contents are, right?

 8232 tty1     S      0:00  \_ -bash
 8248 tty1     S+     0:00      \_ /bin/sh /usr/sbin/ltsp-update-image
 8259 tty1     Sl+    9:22          \_ mksquashfs /opt/ltsp/i386 /opt/ltsp/images/i386.img.tmp -e cdrom

sauer@midnight:~$ du -hs /opt/ltsp/images/i386.img.tmp 
391M    /opt/ltsp/images/i386.img.tmp

sauer@midnight:~$ df -h /opt/ltsp/images/ /tmp
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/midnight-ltsp
                      3.0G  1.5G  1.6G  48% /opt/ltsp
/dev/mapper/midnight-tmp
                       24G   33M   24G   1% /tmp

---

### Post by laga on 2008-08-04
Woah, nice setup.

Not sure what to do off-hand.. maybe you can strace the process to see where it's hanging?

---

### Post by db260179 on 2008-08-04
Not sure if it has been fixed yet, but this might help you

[https://bugs.launchpad.net/ubuntu/+source/squashfs/+bug/222700](https://bugs.launchpad.net/ubuntu/+source/squashfs/+bug/222700)

> **dannysauer said:**
> So, the image was initially created fine by ltsp-build-image.  I booted from it, everything was grand.  I then added the ldap client auth stuff, added a couple of NFS mounts to the fstab, and modified a couple of UIDs and GIDs within the chroot to match ldap.  I also removed /var/cache/apt/archives in the chroot since that's NFS mounted on the client.  Now, when I run ltsp-update-image (with no args), mksquashfs gets to 92% and hangs there.  It's been there for almost 24 hours now, so it's not just my impatience. :)

Is there a way to turn up the verbosity so I can see what's happening?  Is this something expected?  I'd blame the removal of apt-cache, but mksquashfs just bundles the folder up without regard to what the contents are, right?

 8232 tty1     S      0:00  \_ -bash
 8248 tty1     S+     0:00      \_ /bin/sh /usr/sbin/ltsp-update-image
 8259 tty1     Sl+    9:22          \_ mksquashfs /opt/ltsp/i386 /opt/ltsp/images/i386.img.tmp -e cdrom

sauer@midnight:~$ du -hs /opt/ltsp/images/i386.img.tmp 
391M    /opt/ltsp/images/i386.img.tmp

sauer@midnight:~$ df -h /opt/ltsp/images/ /tmp
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/midnight-ltsp
                      3.0G  1.5G  1.6G  48% /opt/ltsp
/dev/mapper/midnight-tmp
                       24G   33M   24G   1% /tmp

---

### Post by dannysauer on 2008-08-04
> **db260179 said:**
> Not sure if it has been fixed yet, but this might help you

[https://bugs.launchpad.net/ubuntu/+source/squashfs/+bug/222700](https://bugs.launchpad.net/ubuntu/+source/squashfs/+bug/222700)

This is a multiprocessor system, so that may be related.  I'll edit the code and see if I can add --no-sparse to the mksquashfs command line, and see if that's the issue.  Thanks!

---

### Post by dannysauer on 2008-08-05
> **dannysauer said:**
> This is a multiprocessor system, so that may be related.  I'll edit the code and see if I can add --no-sparse to the mksquashfs command line, and see if that's the issue.  Thanks!

Ok, it's replicable by just running the command (with a different destination):

sauer@midnight:~$ sudo mksquashfs /opt/ltsp/i386 /tmp/deleteme -e cdrom
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on /tmp/deleteme, block size 131072.
[=======================================================     ] 54240/58828  92%

Adding -no-sparse *before* the -e cdrom (it's important - doesn't work the other way) lets it run to completion.  So, because there's no config file, I edited /usr/sbin/ltsp-update-image (line 94) to include -no-sparse, and it's working just fine now.

I also did a run with the -info switch in there, to find out what's triggering it.

mksquashfs: file /opt/ltsp/i386/var/lib/apt/lists/lock, uncompressed size 0 bytes 

So, mksquashfs is finding a 0-byte lock file for the package lists, and treating it as "sparse".  This would probably be fine if the lock file is removed.

---

### Post by ttabbal on 2008-12-11
I ran into this today. Thanks for posting the fix, it worked for me as well.

---

