---
title: "System messed up after enabling DVD playback."
date: 2009-12-20
forum: Multimedia Software
---

### Post by mpiroc on 2009-12-20
A friend running Ubuntu 9.10 asked me how to enable DVD playback. I directed him [to this link]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04%20and%209.10%20(i386,%20amd64)"), and told him to use these commands:
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

He tried this, and ran into some problems:
> I ran into a problem... I entered the "apt-get" command above and I got a nfs-common error. Now I can add/remove programs, update with out seeing errors occuring. I looked up the bug on ubuntuforums.org, but I don't quite see how a "fix" is to be installed. Is there a way to go back to a date when the error didn't occur? Or is there a way to have errors evaluated (system check) with fixes recommended?

I asked him for a copy of the error, and he sent me these:

```
Here is a copy of the listing from the details of an error message while I was attempting to get OpenOffice's data management (like MS Access)
--------------------------

Adding system user `statd' (UID 116) ...
Adding new user `statd' (UID 116) with group `nogroup' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/nfs -g nogroup -s /bin/false -u 116 statd' returned error code 1. Exiting.
dpkg: error processing nfs-common (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
dependency problems - leaving unconfigured
Setting up libservlet2.4-java (5.0.30-8ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up libhsqldb-java (1.8.0.10-2ubuntu1) ...

Setting up openoffice.org-java-common (1:3.1.1-5ubuntu1) ...

Setting up openoffice.org-base (1:3.1.1-5ubuntu1) ...

Errors were encountered while processing:
nfs-common
nfs-kernel-server
```

and

```
Here is the complete text from an error after entering...
[his name]@[his name]-laptop:~$ sudo apt-get install libdvdread4
[sudo] password for todd: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nfs-common (1:1.2.0-2ubuntu8) ...
Adding system user `statd' (UID 116) ...
Adding new user `statd' (UID 116) with group `nogroup' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/nfs -g nogroup -s /bin/false -u 116 statd' returned error code 1. Exiting.
dpkg: error processing nfs-common (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
nfs-common
nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

All this is a bit beyond my knowledge of Ubuntu. Any idea what's going on?

---

### Post by mpiroc on 2009-12-21
If this is not enough information to help someone figure this out, can you let me know what you need?

---

