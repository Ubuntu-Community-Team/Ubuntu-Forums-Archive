---
title: "Need help building cisco vpn client"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by bkline on 2012-12-28
I'm trying to build and install Cisco's client from source on Ubuntu 12.04.  I have the correct kernel source headers (3.2.0-35-generic) installed.  Here are the errors I'm getting:
```
$ tar xzf vpnclient-linux-x86_64-4.8.02.0030-k9-nih.tar.gz
$ cd vpnclient
$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/3.2.0-35-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/3.2.0-35-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/3.2.0-35-generic/build" will be used to build the module.

Is the above correct [y]

Making module
linuxcniapi.c:14:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
interceptor.c:13:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
IPSecDrvOS_linux.c:16:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
frag.c:3:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
In file included from linuxkernelapi.c:1:0:
/lib/modules/3.2.0-35-generic/build/include/linux/string.h:21:24: fatal error: asm/string.h: No such file or directory
compilation terminated.
ld: cannot find linuxkernelapi.o: No such file or directory
ld: cannot find frag.o: No such file or directory
ld: cannot find linuxcniapi.o: No such file or directory
ld: cannot find IPSecDrvOS_linux.o: No such file or directory
ld: cannot find interceptor.o: No such file or directory
Failed to make module "cisco_ipsec".

```

Any suggestions on how to fix the errors?  I cant use the vpnc that's in the repository, because one of my customers has switched to requiring 2-step authentication with a card reader.

Many thanks!

---

### Post by srekcahrai on 2012-12-28
Maybe the files don't have permission. Try this
$ tar xzf vpnclient-linux-x86_64-4.8.02.0030-k9-nih.tar.gz
$ sudo chmod -R u+rwx vpnclient-linux-x86_64-4.8.02.0030-k9-nih
$ cd vpnclient
$ sudo ./vpn_install

---

### Post by bkline on 2012-12-28
> **srekcahrai said:**
> Maybe the files don't have permission. Try this
$ tar xzf vpnclient-linux-x86_64-4.8.02.0030-k9-nih.tar.gz
$ sudo chmod -R u+rwx vpnclient-linux-x86_64-4.8.02.0030-k9-nih
$ cd vpnclient
$ sudo ./vpn_install

Thanks for the reply, but I'm running the build as root, and all of the files are already world-readable, all of the directories world-searchable, and all of the scripts and programs already world-executable.

---

### Post by bkline on 2012-12-28
Hacking away at the problem, making a little bit of progress.

By modifying four of the five .c files, and replacing
```
#include <linux/autoconf.h>
``` with ```
#include <generated/autoconf.h>
``` I was able to eliminate the error at the top of my first post in the thread (which caused the other errors in a cascade).  Now the error is that the compiler finds linux/linkage.h, but that in turn includes asm/linkage.h, which the compiler can't find.  I'm tempted to either add a soft link from /lib/modules/3.2.0-35-generic/build/include/asm to /lib/modules/3.2.0-35-generic/build/arch/x86/include/asm (which is in turn a soft link itself) or to add another INCLUDE location to the build script, though I'm made a little nervous by the fact that such a problem needs to be solved at all.  I mean, it's one thing to have source code from a third part (Cisco in this case) which has an out-of-date notion of how the include files are laid out on a linux machine, but this is one header from the Ubuntu repository unable to find another header from the same repository.

Any advice from the gurus would be gratefully received!

---

