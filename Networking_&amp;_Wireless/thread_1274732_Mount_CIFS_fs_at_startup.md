---
title: "Mount CIFS fs at startup"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by dragonfrog on 2009-09-24
Hello all

I'm running Ubuntu 9.04 on an Intel iMac.  I'm trying to mount a CIFS share on one of those little Buffalo NAS boxes (putting at /var/backup to use it with simple backup).  At first I just put an entry in /etc/fstab like this:

```
//Lefty/mark_folder/backups /var/backup smbfs credentials=/etc/fstab.mark.creds,uid=root,rw    0    0

```Which resulted  in a hanging process at boot, which I had to interrupt with ctrl-alt-del.

Then I tried adding the *_netdev* option to the entry, which is supposed to prevent it from trying to mount before the network is ready, but that didn't work.

Then I added *noauto* to the entry, so it doesn't mount with the rest of the filesystems, and try to mount it right at the very end of booting, with /etc/rc.local.  My /etc/rc.local looks like:

```

#!/bin/sh

echo rc.local running $(date) >> /home/mark/rc.local.run

mount /var/backup >> /home/mark/rc.local.run 2>&1

echo exit status $? >> /home/mark/rc.local.run

exit 0
```So in principle the network should definitely be ready by then.  But rc.local.run is full of this:

```
rc.local running Wed Sep 23 22:34:19 MDT 2009
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
exit status 32
rc.local running Thu Sep 24 19:18:53 MDT 2009
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
exit status 32

```If I wait until after boot, and run rc.local manually (as root), the file system mounts fine, and I get no errors in the log, just an entry like this:

```
rc.local running Tue Sep 22 21:00:10 MDT 2009
exit status 0

```

Thanks in advance for any help or advice you can give me.

---

### Post by Iowan on 2009-09-24
I suspect you have probably seen [this]("http://ubuntuforums.org/showthread.php?t=288534") one, but just in case...

---

### Post by dragonfrog on 2009-09-25
Thanks Iowan - I had seen that post along with a bunch of other partially contradictory ones - looks like that one is a good'un!

So, having added windind and changed /etc/nsswitch.conf as described there (and removed the noauto option from the fstab entry), I still get the hanging mount process on boot, have to kill it with ctrl-alt-del, but by the time I've logged in, the CIFS mount has worked.

I'm not exactly sure how though - rc.local.run still shows the same errors...  Ah well, I'm ahead of where I was!

Cheers
Mark

---

