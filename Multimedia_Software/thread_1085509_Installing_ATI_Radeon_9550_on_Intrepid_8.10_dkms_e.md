---
title: "Installing ATI Radeon 9550 on Intrepid 8.10 dkms error"
date: 2009-03-03
forum: Multimedia Software
---

### Post by kmacphail on 2009-03-03
I am having major problems getting my graphics card Radeon 9550 to work with Ubuntu 8.10 Intrepid.

I have attempted to install the driver from the ATI site, however when I run through the installation I get this message at the end:

[I]DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.Eg9865[/I]

I looked in the fglrx-install.log and it contained this info:


[I]Creating symlink /var/lib/dkms/fglrx/8.582/source ->
                 /usr/src/fglrx-8.582

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located.
[Error] Kernel Module : Failed to build fglrx-8.582 with DKMS
[Error] Kernel Module : Removing fglrx-8.582 from DKMS[/I]

Modprob gives me the line:

*FATAL: Module fglrx not found. *

So I then removed the driver and extracted the deb files from the driver using the *--buildpkg Ubuntu/intrepid* command.  This went as promised by creating several deb packages. However when I try and install the packages using the *dpkg -i* command I get the following errors:

[I]Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (i686) first.
Done.[/I]

Please help as I have been working on this since last saturday and it is driving me mad.

---

### Post by Roving Sign on 2009-03-03
> **kmacphail said:**
> I am having major problems getting my graphics card Radeon 9550 to work with Ubuntu 8.10 Intrepid.

I have attempted to install the driver from the ATI site, however when I run through the installation I get this message at the end:

[I]DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.Eg9865[/I]

I looked in the fglrx-install.log and it contained this info:


[I]Creating symlink /var/lib/dkms/fglrx/8.582/source ->
                 /usr/src/fglrx-8.582

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located.
[Error] Kernel Module : Failed to build fglrx-8.582 with DKMS
[Error] Kernel Module : Removing fglrx-8.582 from DKMS[/I]

Modprob gives me the line:

*FATAL: Module fglrx not found. *

So I then removed the driver and extracted the deb files from the driver using the *--buildpkg Ubuntu/intrepid* command.  This went as promised by creating several deb packages. However when I try and install the packages using the *dpkg -i* command I get the following errors:

[I]Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (i686) first.
Done.[/I]

Please help as I have been working on this since last saturday and it is driving me mad.

Cant help with that specifically...but

I have a 9550 and it really didnt work that well with the ATI driver...

(I think I found out support for FGLRX runs out around the 9220 series?)

Fullscreen video was really choppy...worked much better with whatever the stock driver is...

Edit: you can install the ATI driver via Synaptic, but have to have certain repositories enabled...

---

