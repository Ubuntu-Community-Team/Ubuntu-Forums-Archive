---
title: "apt-get/dpkg (control file not found)"
date: 2009-03-22
forum: Mythbuntu
---

### Post by mbondfusion on 2009-03-22
An error occurred while upgrading packages.  I tried using 'dpkg' with the same results.  The '.deb' file is not corrupt as far as I can tell (downloaded from archive.ubuntu.com).  It happens with all 29 packages pending upgrade.  I tried 'apt-get -f install', 'apt-get clean', and 'apt-get autoclean'.  Hope I don't have to reinstall.

_cmd:_
sudo apt-get upgrade

_output:_
[SIZE="1"]Preconfiguring packages ...
dpkg: error processing /var/cache/apt/archives/dash_0.5.4-9ubuntu1.1_i386.deb (--unpack):
 failed to open package info file `/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/dash_0.5.4-9ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE]


_cmd:_
dpkg -I dash_0.5.4-9ubuntu1.1_i386.deb

_output:_
[SIZE="1"] new debian package, version 2.0
 size 90266 bytes: control archive= 2905 bytes.
(no `control' file in control archive!)[/SIZE]

[SOLUTION]
After reviewing several strace logs from 'dpkg -I', 'dpkg -e', etc... I concluded that dpkg was unable to spawn /bin/tar.
After seeing that tar was 0 (zero) bytes.  I replaced it and now 'apt-get upgrade' finished successfully.

---

