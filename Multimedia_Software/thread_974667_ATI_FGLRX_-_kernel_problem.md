---
title: "ATI FGLRX - kernel problem?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by petersk on 2008-11-07
I get an unusual message when trying to update to the proprietary ATI driver; it seems there's something wrong with the way my kernel's installed, cdbs is installed, or dkms is installed. If someone has any suggestions, please help.  I'm using an ATI x1600 card , AGP.

Below is the interaction:

root# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx xorg-driver-fglrx-dev
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 78.6kB/20.1MB of archives.
After this operation, 950kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted xorg-driver-fglrx-dev 2:8.543-0ubuntu4 [78.6kB]
Fetched 78.6kB in 1s (69.3kB/s)
(Reading database ... 195434 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 2:8.542-0ubuntu1 (using .../fglrx-kernel-source_2%3a8.543-0ubuntu4_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
dpkg: warning - unable to delete old directory `/usr/src/fglrx-8.542': Directory not empty
Preparing to replace xorg-driver-fglrx 2:8.542-0ubuntu1 (using .../xorg-driver-fglrx_2%3a8.543-0ubuntu4_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace fglrx-amdcccle 2:8.542-0ubuntu1 (using .../fglrx-amdcccle_2%3a8.543-0ubuntu4_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace xorg-driver-fglrx-dev 2:8.542-0ubuntu1 (using .../xorg-driver-fglrx-dev_2%3a8.543-0ubuntu4_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Preparing to replace fglrx-modaliases 2:8.542-0ubuntu1 (using .../fglrx-modaliases_2%3a8.543-0ubuntu4_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Processing triggers for man-db ...
Setting up fglrx-kernel-source (2:8.543-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build

Error! Your kernel source for kernel 2.6.27-7-server cannot be found at
/lib/modules/2.6.27-7-server/build or /lib/modules/2.6.27-7-server/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-server (i686) first.
Done.

Setting up xorg-driver-fglrx (2:8.543-0ubuntu4) ...
Installing new version of config file /etc/ati/atiogl.xml ...
Installing new version of config file /etc/ati/signature ...
Installing new version of config file /etc/ati/authatieventsd.sh ...

Setting up fglrx-amdcccle (2:8.543-0ubuntu4) ...
Setting up xorg-driver-fglrx-dev (2:8.543-0ubuntu4) ...
Setting up fglrx-modaliases (2:8.543-0ubuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Kurt

---

### Post by petersk on 2008-11-08
I ended up using Synaptic to uninstall the server kernel.  I then reinstalled the generic one.  All seemed to work pretty well after that change.
Kurt

---

### Post by virtudtierra on 2008-11-09
I've a related trouble...

my xorg server crash after games on fullscreen modes!... i've to install the driver following [this tutorial]("http://64.233.169.104/search?q=cache:_qJDcqBQcRoJ:www.ubuntu-es.org/index.php%3Fq%3Dnode/101927+ati+200M+ubuntu+8.10&hl=es&ct=clnk&cd=1&gl=cl&client=firefox-a"). 

I've to do this because i had the same troubles!!!... now, the graphical aceleration works, but after fullscreen modes of NEXUIZ, the xorg server crash!

any idea to make it work normally?

thanks!

Jorge

---

