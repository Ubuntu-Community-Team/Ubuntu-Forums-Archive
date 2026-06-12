---
title: "Netflix-Desktop extended filesystem attributes errors"
date: 2013-09-15
forum: Multimedia Software
---

### Post by radiowave911 on 2013-09-15
Having seen a number of people apparently having great success using Netflix Desktop to watch Netflix, I decided to give it a whirl.  I followed the instructions to add the PPA and install Netflix-Desktop (it also installed a Wine Silverlight installer).  All of the instructions say that the rest of what is needed will install when I launch Netflix Desktop the first time.  Fair enough.  Except it does not launch.  I receive the following error:

It appears that you do not have extended file system attributes enabled. Please enable the user_xattr option for your filesystem and try again.

So I look this up.  The references I find indicate that this can occur with an EXT3 FS.  Mine is EXT4.  I tried anyway.  From my fstab:
```

root@ubuntustudio:/# more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f4eb171f-62ad-4ed7-8cf9-e8a58ad2517a /               ext4    errors=remount-ro,user_xattr	0       1
# /home was on /dev/sdb1 during installation
UUID=8b366d73-52d5-407c-b161-504de10bc7e7 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda1 during installation
UUID=feb19837-4136-468d-a557-a7c539f946ba none            swap    sw              0       0

```
and if I look to see what is currently mounted:
```

root@ubuntustudio:/# mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /home type ext4 (rw,user_xattr)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/radiowave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=radiowave)

```
One other item I found suggested removing ~/.netflix-desktop.  It does not exist on this system:

```

radiowave@ubuntustudio:~$ ls -al | grep -i net
drwxrwxr-x   4 radiowave radiowave         4096 Nov  5  2012 .netbotz
drwxrwxr-x   3 radiowave radiowave         4096 Nov  5  2012 NetBotz
lrwxrwxrwx   1 radiowave radiowave           58 Nov  5  2012 NetBotz_Advanced_View-2.6 -> /home/radiowave/NetBotz/av/linux/NetBotz_Advanced_View_2.6
-rw-r--r--   1 radiowave radiowave       188073 Jan 21  2012 winetricks
-rw-r--r--   1 radiowave radiowave          322 Jan 21  2012 wireless_network_settings

```
As an aside, in spite of the 'ubuntustudio' hostname, this is not running ubuntustudio.  I just kept the name when I rebuilt from scratch the last time.  This is running Ubuntu 12.04LTS, 64-Bit.

In addition to the above, I have tried uninstalling/reinstalling Netflix-Desktop, and purging/reinstalling Netflix-Desktop.  I am now stuck.  Any suggestions would be helpful.  I will provide whatever additional information is necessary, to assist in troubleshooting, short of account details of course :)

---

### Post by radiowave911 on 2013-09-15
I may be on to a solution.  It involves an edit to the script /usr/share/wine-browser-installer/test-xattr....stay tuned :)

If this works, I will post the details.

---

### Post by radiowave911 on 2013-09-15
Much closer.  It launches now, it installed what it had to.

I was directed to a pose here: [http://www.ubuntuupdates.org/ppa/ehoover_compholio_netflix](http://www.ubuntuupdates.org/ppa/ehoover_compholio_netflix)

Reading the comments on the post, it seems that a change needed to be made to the script /usr/share/wine-browser-installer/test-xattr.  Specifically, the xattr.set and xattr.get needed to be changed to xattr.setxattr and xattr.getxattr.

The original looked like this:
```

#!/usr/bin/env python

import xattr
import os
import sys

try:
    os.chdir(sys.argv[1])
except:
    print "Usage: test-xattr <directory>"
    sys.exit(3)

fname = 'xattr.%d' % os.getpid()
open(fname, 'w').close()
try:
    xattr.set(fname, 'user.comment', 'test')
    value = xattr.get(fname, 'user.comment')
    rc = 0 if value == 'test' else 1
except:
    rc = 2
finally:
    os.unlink(fname)
sys.exit(rc)

```
Modified (working):
```

#!/usr/bin/env python

import xattr
import os
import sys

try:
    os.chdir(sys.argv[1])
except:
    print "Usage: test-xattr <directory>"
    sys.exit(3)

fname = 'xattr.%d' % os.getpid()
open(fname, 'w').close()
try:
    xattr.setxattr(fname, 'user.comment', 'test')
    value = xattr.getxattr(fname, 'user.comment')
    rc = 0 if value == 'test' else 1
except:
    rc = 2
finally:
    os.unlink(fname)
sys.exit(rc)

```

Thanks to sgrunt on the forums at userfriendly.org for pointing me in the right direction and helping me find this solution!

---

