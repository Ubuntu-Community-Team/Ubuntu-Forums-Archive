---
title: "Problems upgrading udev"
date: 2011-03-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cmccauley on 2011-03-01
Hi,

I'm getting a nasty problem with a udev upgrade (see below) which has failed. Anyone know how to resolved this dpkg-divert problem? Is it a good idea to do a dpkg-divert --remove ?

Thanks

Chris



[FONT="Courier New"]The following partially installed packages will be configured:
  initramfs-tools udisks 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/340 kB of archives. After unpacking 0 B will be used.
(Reading database ... 334312 files and directories currently installed.)
Preparing to replace udev 166-0ubuntu2 (using .../udev_166-0ubuntu2_i386.deb) ...
dpkg-divert: error: `diversion of /sbin/udevadm to /sbin/udevadm.upgrade by udev' clashes with `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
dpkg: error processing /var/cache/apt/archives/udev_166-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg-divert: error: mismatch on package
  when removing `diversion of /sbin/udevadm to /sbin/udevadm.upgrade by udev'
  found `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/udev_166-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not installed.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udisks:
 udisks depends on udev; however:
  Package udev is not installed.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 udisks
[/FONT]

---

### Post by jppr on 2011-03-01
[https://launchpad.net/ubuntu/natty/+source/udev/166-0ubuntu3](https://launchpad.net/ubuntu/natty/+source/udev/166-0ubuntu3)

---

### Post by jorb on 2011-03-01
```
dpkg-divert --remove '/sbin/udevadm'
```worked for me

---

### Post by cmccauley on 2011-03-02
Worked for me too!

Unfortunately (and unrelated) now I have no window manager on reboot :-(

---

### Post by Harry33 on 2011-03-02
> **cmccauley said:**
> Worked for me too!

Unfortunately (and unrelated) now I have no window manager on reboot :-(

Have you tried installing the latest version of udev (166-0ubuntu3)?
This problem with -local diversions is fixed there.

---

