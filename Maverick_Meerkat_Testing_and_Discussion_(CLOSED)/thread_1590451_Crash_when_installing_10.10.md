---
title: "Crash when installing 10.10"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by chrisrx on 2010-10-07
I have been running ubuntu on my netbook but it was starting to get a bit cluttered with programs I didn't use any more so I decided to format and start over with 10.10.  When I try to install the latest RC from USB though, the installer crashes after it is done copying files and starts scanning the USB for packages.
My drive is partitioned with a 10GB partition for ubuntu, 10GB for windows and the rest for storage.  Here is the last part of the syslog.  The errors seem to start when it can't find a file for some reason.  After that it looks like it tries to resize my NTFS data partition for some reason even though I have not specified the NTFS partition to be changed at all.
Does anyone have any idea what is going wrong?

```
Oct  8 01:33:47 ubuntu in-target: Reading package lists...
Oct  8 01:33:48 ubuntu in-target: 
Oct  8 01:33:48 ubuntu apt-setup: Using CD-ROM mount point /cdrom/
Oct  8 01:33:48 ubuntu apt-setup: Identifying.. 
Oct  8 01:33:48 ubuntu apt-setup: [168d3e10e3518ae33ad8f43ca6cf45f6-2]
Oct  8 01:33:48 ubuntu apt-setup: Scanning disc for index files..
Oct  8 01:33:50 ubuntu apt-setup: Found 2 package indices, 1 source indices, 0 translation indices and 1 signatures
Oct  8 01:33:50 ubuntu apt-setup: Found label: Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release Candidate i386 (20100928.2)
Oct  8 01:33:50 ubuntu apt-setup: This disc is called: 
Oct  8 01:33:50 ubuntu apt-setup: 'Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release Candidate i386 (20100928.2)'
Oct  8 01:33:50 ubuntu apt-setup: Copying package lists...
Oct  8 01:33:50 ubuntu apt-setup: gpgv: Signature made Tue 28 Sep 2010 13:49:13 UTC using DSA key ID FBB75451
Oct  8 01:33:50 ubuntu apt-setup: gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Oct  8 01:33:50 ubuntu apt-setup: #015Reading Package Indexes... 0%#015
Oct  8 01:33:50 ubuntu apt-setup: #015Reading Package Indexes... 1%#015
Oct  8 01:33:50 ubuntu apt-setup: #015Reading Package Indexes... Done#015
Oct  8 01:33:50 ubuntu apt-setup: W
Oct  8 01:33:50 ubuntu apt-setup: : Skipping nonexistent file /cdrom/dists/maverick/main/binary-i386/Packages
Oct  8 01:33:50 ubuntu apt-setup: W: Skipping nonexistent file /cdrom/dists/maverick/restricted/binary-i386/Packages
Oct  8 01:33:50 ubuntu apt-setup: E: Read error - read (21: Is a directory)
Oct  8 01:34:37 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Oct  8 01:34:37 ubuntu apt-setup: warning: /usr/lib/ubiquity/apt-setup/generators/40cdrom returned error code 1; discarding output
Oct  8 01:34:38 ubuntu choose-mirror[26073]: INFO: base system installable from CD; skipping mirror check
Oct  8 01:34:38 ubuntu choose-mirror[26073]: INFO: falling back to codename maverick
Oct  8 01:34:38 ubuntu ubiquity: cp: 
Oct  8 01:34:38 ubuntu ubiquity: cannot create regular file `/target/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_Release.gpg'
Oct  8 01:34:38 ubuntu ubiquity: : No such file or directory
Oct  8 01:34:38 ubuntu ubiquity: 
Oct  8 01:34:38 ubuntu apt-setup: warning: /usr/lib/ubiquity/apt-setup/generators/50mirror.ubuntu returned error code 1; discarding output
Oct  8 01:34:38 ubuntu ubiquity: chroot: 
Oct  8 01:34:38 ubuntu ubiquity: failed to run command `tempfile'
Oct  8 01:34:38 ubuntu ubiquity: : No such file or directory
Oct  8 01:34:38 ubuntu ubiquity: 
Oct  8 01:34:38 ubuntu ubiquity: umount: /target/cdrom: not found
Oct  8 01:34:38 ubuntu ubiquity: 
Oct  8 01:34:38 ubuntu python: log-output -t ubiquity umount /target/cdrom
Oct  8 01:34:38 ubuntu ubiquity: grep: 
Oct  8 01:34:38 ubuntu ubiquity: /target/etc/apt/sources.list
Oct  8 01:34:38 ubuntu ubiquity: : No such file or directory
Oct  8 01:34:38 ubuntu ubiquity: 
Oct  8 01:34:38 ubuntu python: Exception during installation:
Oct  8 01:34:38 ubuntu python: Traceback (most recent call last):
Oct  8 01:34:38 ubuntu python:   File "/usr/share/ubiquity/plugininstall.py", line 1424, in <module>
Oct  8 01:34:38 ubuntu python:     install.run()
Oct  8 01:34:38 ubuntu python:   File "/usr/share/ubiquity/plugininstall.py", line 54, in wrapper
Oct  8 01:34:38 ubuntu python:     func(self)
Oct  8 01:34:38 ubuntu python:   File "/usr/share/ubiquity/plugininstall.py", line 136, in run
Oct  8 01:34:38 ubuntu python:     self.configure_apt()
Oct  8 01:34:38 ubuntu python:   File "/usr/share/ubiquity/plugininstall.py", line 438, in configure_apt
Oct  8 01:34:38 ubuntu python:     raise install_misc.InstallStepError("AptSetup failed with code %d" % ret)
Oct  8 01:34:38 ubuntu python: InstallStepError: AptSetup failed with code 127
Oct  8 01:34:38 ubuntu python: 
Oct  8 01:34:44 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct  8 01:34:44 ubuntu ntfsresize: Device name        : /dev/sda5
Oct  8 01:34:44 ubuntu ntfsresize: NTFS volume version: 3.1
Oct  8 01:34:44 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct  8 01:34:44 ubuntu ntfsresize: Current volume size: 10487198208 bytes (10488 MB)
Oct  8 01:34:44 ubuntu ntfsresize: Current device size: 10487199744 bytes (10488 MB)
Oct  8 01:34:44 ubuntu ntfsresize: Checking filesystem consistency ...
Oct  8 01:34:44 ubuntu ntfsresize: Accounting clusters ...
Oct  8 01:34:44 ubuntu ntfsresize: Space in use       : 9929 MB (94.7%)
Oct  8 01:34:44 ubuntu ntfsresize: Collecting resizing constraints ...
Oct  8 01:34:44 ubuntu ntfsresize: You might resize at 9928065024 bytes or 9929 MB (freeing 559 MB).
Oct  8 01:34:44 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct  8 01:34:46 ubuntu ubiquity[20266]: switched to page partman
```

---

### Post by chrisrx on 2010-10-08
I just tried to install using the latest daily build instead of the RC (which shouldn't really be that much different) and it still crashes at the same place after the message > An attempt to configure apt to install additional packages from the CD failed.
I've looked this up on the net and it seems that whenever someone gets the message the installation carries on fine anyway.

---

### Post by chrisrx on 2010-10-09
Sorry if bumping is not allowed has no-one actually got any idea?

---

### Post by Speed_arg on 2010-10-09
They wont mind, now ubuntu seems to care more about eye candy and releasing in a day which looks fashion (10 10 10) than releasing a polished version without this awful bugs. Installer doesnt work for me neither, although I get a different error.

---

### Post by cariboo on 2010-10-09
It looks like your problem is with your ntfs partition. I would suggest you run chkdsk on your windows partition, then try installing again.

@Speed_arg, you keep making these comments, but you never provide any information, if you want help, you have to give us details. Let us know what hardware and what error messages you are getting.

---

### Post by Speed_arg on 2010-10-09
> **cariboo907 said:**
> It looks like your problem is with your ntfs partition. I would suggest you run chkdsk on your windows partition, then try installing again.

@Speed_arg, you keep making these comments, but you never provide any information, if you want help, you have to give us details. Let us know what hardware and what error messages you are getting.

[http://ubuntuforums.org/showthread.php?t=1588391](http://ubuntuforums.org/showthread.php?t=1588391) this is the thread in which i posted the bug. The hardware is mentioned there Asus 1005HA (n270 1gb ram).

I get no error messages.

---

