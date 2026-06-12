---
title: "OSS 4.0 won't start"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by ggore on 2007-03-20
Running Edgy, I installed the new OSS 4.0 that is supposed to work with X-Fi sound cards.  Installation completed with the following:

Preparing to replace oss-linux v4.0-1000 (using oss-linux_v4.0-1000_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1000_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.17-11-386
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux_v4.0-1000_i386.deb

So I removed the "starting" file, ran soundon like it requested, and received the following message:

/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 31: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 33: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 35: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 41: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 41: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 48: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue

What am I doing wrong?  It says OSS is installed but evidently something it very wrong.  
Thanks.

---

