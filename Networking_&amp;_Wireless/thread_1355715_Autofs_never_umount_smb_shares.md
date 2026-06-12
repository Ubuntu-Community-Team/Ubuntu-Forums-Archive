---
title: "Autofs never umount smb shares"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by oscar69 on 2009-12-15
I've succesfully configured smb shares to automount with autofs, but after the timeout the shares are still there, never umounted.

Also, trying to stop the autofs I got error:

```
root@oscar-desktop:/etc# /etc/init.d/autofs stop
Stopping automounter:Stopped automount (pid 22200).
Program automount, 1 process(es), refused to die.

  Couldn't stop automount for /mnt done.
root@oscar-desktop:/etc#
```

If I umount shares by-hand, after the defined timeout, server folder disappears, as expected.

In details:

```

/etc/hosts contain
192.168.0.2       nas

cat /etc/auto.master 
/mnt/   /etc/auto.smb

cat /etc/auto.smb.nas
username=oscar
password=123456

```

Then:

```
root@oscar-desktop:/etc# /etc/init.d/autofs start
Starting automounter: done.
root@oscar-desktop:/etc# /etc/init.d/autofs status
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 /mnt program /etc/auto.smb

Active Mount Points:
--------------------
/usr/sbin/automount --pid-file=/var/run/autofs/_mnt.pid --timeout=300 /mnt program /etc/auto.smb

root@oscar-desktop:/etc# ls /mnt/
root@oscar-desktop:/etc#

```

This sounds correct, shares not yet mounted, and option ghost not specified

```

root@oscar-desktop:/etc# ls /mnt/nas
info  share  usbdisk2
root@oscar-desktop:/etc#

```

This also sounds correct, accessing folder shares are mounted

```

root@oscar-desktop:/etc# date
mar dic 15 14:26:18 CET 2009

```

Now wait for timeout...

```
root@oscar-desktop:/etc# date
mar dic 15 14:31:42 CET 2009

```

Shares are still there:

```

root@oscar-desktop:/etc# ls /mnt
nas
root@oscar-desktop:/etc# mount
automount(pid22351) on /mnt type autofs (rw,fd=4,pgrp=22351,minproto=2,maxproto=4)
//nas/info on /mnt/nas/info type cifs (rw,mand)
//nas/share on /mnt/nas/share type cifs (rw,mand)
//nas/usbdisk2 on /mnt/nas/usbdisk2 type cifs (rw,mand)

```

Now, umount shares by hand:

```
root@oscar-desktop:/etc# umount /mnt/nas/share
root@oscar-desktop:/etc# umount /mnt/nas/info
root@oscar-desktop:/etc# umount /mnt/nas/usbdisk2

root@oscar-desktop:/etc# mount
automount(pid22351) on /mnt type autofs (rw,fd=4,pgrp=22351,minproto=2,maxproto=4)

root@oscar-desktop:/etc# ls /mnt/
nas

root@oscar-desktop:/etc# date
mar dic 15 14:35:34 CET 2009

```

Again, wait for timeout...

```
root@oscar-desktop:/etc# date
mar dic 15 14:41:46 CET 2009

root@oscar-desktop:/etc# ls /mnt
root@oscar-desktop:/etc#

```

Share's server disappear, as expected.

The problem is that I'd like to auto umount also shares, that are child of nas server: they are the shares exported from the server. 
The auto.smb script look the server to discover them, and mount all of it.

Seems that automount wait the /mnt/nas is free, but its child are the interesting folders, and nobody is there to umount them... :(

I've also tryed without the auto.smb script:

```

root@oscar-desktop:/etc# cat auto.master
/mnt    /etc/auto.nas

root@oscar-desktop:/etc# cat auto.nas
share           -fstype=smbfs,username=oscar,password=123456,rw        ://nas/share

```

But it's the same: obviously there isn't the "nas" folder, but the mountpoint never disappears, and it's impossible to stop autofs process, just like with auto.smb: seems that is wait as free the /mnt folder, and not the /mnt/share :(

Any suggestion?

---

### Post by oscar69 on 2009-12-17
I found that the autofs5 works correctly.

However, I not used the auto.smb script, becuse it not worked correctly, and I didn't investigated more on it.

Also, I need to comment out the default line in auto.master (I found there is the [bug #488696]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/488696") opened on it.

Instead I used a shell script that return just share info, like as parameters:

```

root@oscar-desktop:~# cat /etc/auto.master
#  +auto.master
/mnt    program:/etc/auto.share

root@oscar-desktop:~# cat /etc/auto.share
#!/bin/bash

echo " -fstype=smbfs,username=oscar,password=123456,rw        ://192.168.0.2/share"

```

---

