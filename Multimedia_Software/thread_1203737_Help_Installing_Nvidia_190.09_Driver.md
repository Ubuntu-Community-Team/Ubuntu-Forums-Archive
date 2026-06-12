---
title: "Help Installing Nvidia 190.09 Driver"
date: 2009-07-03
forum: Multimedia Software
---

### Post by rmtatum on 2009-07-03
I attempted to install the 190.09 driver my Nvidia graphics card.

I received the following output from aptitude: 
```
(Reading database ... 278070 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb) ...
rm: cannot remove `/usr/src/nvidia-185.19.1~really185.18.14': No such file or directory
dpkg: error processing /var/cache/apt/archives/nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package nvidia-180-libvdpau.
Unpacking nvidia-180-libvdpau (from .../nvidia-180-libvdpau_190.09-0ubuntu0_amd64.deb) ...
Selecting previously deselected package nvidia-glx-180.
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_190.09-0ubuntu0_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_180.25-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-settings (180.25-0ubuntu1) ...

dpkg: dependency problems prevent configuration of nvidia-glx-180:
 nvidia-glx-180 depends on nvidia-180-kernel-source (>= 190.09); however:
  Package nvidia-180-kernel-source is not installed.
dpkg: error processing nvidia-glx-180 (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-180-libvdpau (190.09-0ubuntu0) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-glx-180
Press return to continue.

```

How can I fix this problem?

---

### Post by Sub101 on 2009-07-03
I think its due to:

> dpkg: dependency problems prevent configuration of nvidia-glx-180:
 nvidia-glx-180 depends on nvidia-180-kernel-source (>= 190.09); however:
  Package nvidia-180-kernel-source is not installed.


Try installing that, then your new driver.

---

### Post by rmtatum on 2009-07-03
No, that's not the problem.  It tries to install the required package as the output I posted shows.  I just tried running sudo apt-get -f install and it still fails.

```
 sudo apt-get -f install
[sudo] password for username_removed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nvidia-180-kernel-source
The following NEW packages will be installed:
  nvidia-180-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/3361kB of archives.
After this operation, 12.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 278168 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb) ...
rm: cannot remove `/usr/src/nvidia-185.19.1~really185.18.14': No such file or directory
dpkg: error processing /var/cache/apt/archives/nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-180-kernel-source_190.09-0ubuntu0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mc4man on 2009-07-03
Gathering you're using a ppa (M. Marley ?)
did you use his ppa for the previous version  (nvidia-185.19.1~really185.18.14

The preinst for his nvidia- source,,, package is this
> #!/bin/sh
# Copyright (C) 2002-2005 Flavio Stanchina
# Copyright (C) 2005-2006 Aric Cyr
# Copyright (C) 2007 Mario Limonciello
# Copyright (C) 2007 Alberto Milone

rm /usr/src/nvidia-185.19.1~really185.18.14

So if that file doesn't exist the package won't install

Maybe try giving it what it's looking for, (probably doesn't need to be the real file, just a file with the proper name/location.

(otherwise myself, I'd either try editing the preinst (unpack, edit, repack) or just delete it with a archive manager and see what happens, it either installs or it doesn't

---

### Post by rmtatum on 2009-07-03
I was somewhat confused because the package is labeled as 190.09-0ubuntu0.  So, I thought the package was probably an official package.  However, upon reinstalling Ubuntu, I found out that it is actually a ppa package from Michael Marley's PPA (I realized this because I didn't have the gpg for the PPA).  I also encountered the exact same error when trying to install the driver.  So, I found another PPA and the drivers installed fine.

---

### Post by MichalisS on 2009-07-07
> **rmtatum said:**
> I was somewhat confused because the package is labeled as 190.09-0ubuntu0.  So, I thought the package was probably an official package.  However, upon reinstalling Ubuntu, I found out that it is actually a ppa package from Michael Marley's PPA (I realized this because I didn't have the gpg for the PPA).  I also encountered the exact same error when trying to install the driver.  So, I found another PPA and the drivers installed fine.

Could you please specify the PPA's address, because I am experiencing the same problem?

---

