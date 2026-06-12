---
title: "Trying to install video driver"
date: 2013-07-07
forum: Multimedia Software
---

### Post by jgw on 2013-07-07
I have a VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] [1002:5964] (rev 01) and am trying to install a driver.  I have found several files to do this but everytime I try one of them it turns out that its no longer valid, can't find files, etc.  I did goto the radeon driver page and, evidently, this should work but I want to make sure.

I just tried to install as per ask ubuntu.  I downloaded the ati driver, did some suggested stuff and then tried to install.  Everything worked until:
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
Removing temporary directory: fglrx-install.vkOMPq


Thank you...................

---

### Post by BreezyBrooke on 2013-07-07
You can't install drivers for that card anymore. ATI dropped support for that card years ago. Unfortuantly you are stuck with the default driver preloaded by Ubuntu. Sorry.

Ubuntu 10.04 might support the card, but it's End Of Life and therfore not supported itself, so not recommended you install that older version. I'm assuming you are running something like Ubuntu 12.04 or newer, no?

---

### Post by jgw on 2013-07-07
I am running 12.04.2   I went to the ati driver site and they said that the card was supported.  Pretty strange.  I almost got through the installation (I had missed a step <sigh>)  Now I have, in the ati driver folder:
/home/greg/ATI Drivers/amd-driver-installer-12-6-x86.x86_64.run
/home/greg/ATI Drivers/fglrx_8.980-0ubuntu1_i386.deb
/home/greg/ATI Drivers/fglrx-amdcccle_8.980-0ubuntu1_i386.deb
/home/greg/ATI Drivers/fglrx-dev_8.980-0ubuntu1_i386.deb
/home/greg/ATI Drivers/fglrx-installer_8.980-0ubuntu1_i386.changes

I also got an error.  First it tried to report it but the report was rejected.  Then it wanted me to goto support.  I have now stopped.  In theory this board is either a radeon 9200se or a radeon x1300.  My problem is that the motherboard only supports agp which makes it difficult  (I have a pile of those cards which I think I will put up, en-mass, on ebay and get rid of them.  They are simply too marginal.  The built in video, on the card (old SIS) barely even functions.  

Here is where I got the error after the build:
Building initial module for 3.5.0-36-generic
Error! Bad return status for module build on kernel: 3.5.0-36-generic (i686)
Consult /var/lib/dkms/fglrx/8.980/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.980-0ubuntu1) ...
Setting up fglrx-dev (2:8.980-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-36-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
greg@greg-desktop:~/Downloads$ sudo aticonfig --initial -f
aticonfig: No supported adapters detected

Anyway, I was shooting for 3d instead of 2d support and was hoping this card would do the trick.

Thank you for the reply - its appreciated!

---

### Post by Bashing-om on 2013-07-07
jgw; Hi !

There is newly another option: check out:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
This repository provides AMD Catalyst Lagacy 13.1 (fglrx 8.97.100.7) drivers for Radeon HD 2xxx - 4xxx

Looks promising .. and I am aware of 3 people in whom happiness now abounds.

Edit: I am under advisement from knowledgeable sources utilizing this patch is NOT a good idea as it down grades the kernel version. - I stand corrected !

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2013-07-08
> **Bashing-om said:**
> jgw; Hi !

There is newly another option: check out:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
This repository provides AMD Catalyst Lagacy 13.1 (fglrx 8.97.100.7) drivers for Radeon HD 2xxx - 4xxx

That's not going to work for a Radeon 9200SE...

> nyway, I was shooting for 3d instead of 2d support
The default open-source radeon driver does support 3D acceleration.

---

### Post by Bashing-om on 2013-07-08
Temüjin; Thanks ... must have got my wires crossed... 
Will try (again) to be more observant.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

