---
title: "And again bcm4312 and kernel 2.6.29.2"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by narkulome on 2009-05-03
Please help someone!

I downloaded the kernel 2.6.29.2 from [www.kernel.org](www.kernel.org), configured it, included (as I think :) ) all nessesary modules for wifi, and fell into the situation my wifi adapter not working.
Wifi: [I]lspci | grep 4312
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/I]

Trying to compile sta broadcomm driver - getting an error:
[I]...
make[3]: *** [/root/bcm43xx/ndiswrapper/ndiswrapper-1.52/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/root/bcm43xx/ndiswrapper/ndiswrapper-1.52/driver] Error 2
make[2]: Exiting `/usr/src/linux-2.6.29.2'
make[1]: *** [default] Error 2
make[1]: Exiting `/root/bcm43xx/ndiswrapper/ndiswrapper-1.52/driver'
make: *** [install] Error 2[/I]


About wl:
[I]sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module wl not found.
[/I]
About ndiswrapper:
[I]sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.[/I]

I didn't apply any patches to it... But tried to include all the wifi modules when making menuconfig.

Ndiswrapper says when I try to load drivers such a thing:

[I]Module could not be loaded. Error was:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

Is the ndiswrapper module installed?
[/I]
But:

[I]ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4315) present[/I]


Please help someone to clarify this situation... What I am doing wrong...?:confused:
Thanks...

---

### Post by narkulome on 2009-05-03
Ah. also this information:

[I]uname -r
2.6.292-my-custom
[/I]

system: *ubuntu jaunty 9.04*

---

### Post by narkulome on 2009-05-03
Fixed... BUT! In so original way...

First, download the driver from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Then, move it to /*usr/src *and *'cd /usr/src'*
Then, *tar -xzf hybrid-portsrc-x86_32-v5_10_91_9.tar.gz*
Then, *make -C /usr/src/linux-headers-`uname -r` M=`pwd`*
Then, *sudo rmmod wl*
Then, *sudo modprobe lib80211_crypt_tkip*
Then, *sudo modprobe wl*
To see if the errors occur;
After it, *wget [http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/linux-2.6.29.patch](http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/linux-2.6.29.patch)*
*wget [http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/wl_iw_v2.patch](http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/wl_iw_v2.patch)*
*wget [http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/hidden-essid.patch](http://leprosys.net/arch/PKGBUILD/broadcom-wl/files/hidden-essid.patch)*
Then, for SPACE only knows reasons, this string:
*for fn in $(ls *.patch); do patch -p1 < $fn; done*
didn't work, so I applied these three patches manually (they aren't large)
After this,
*make -C /lib/modules/`uname -r`/build M=`pwd`*
*modprobe lib80211_crypt_tkip*
*insmod wl.ko*
*cp wl.ko /lib/modules/`uname -r`/kernel/net/wireless/*
*depmod -a*
*modprobe wl*

And my wifi adapter started finding, found and connected to my home wifi network - all is working good :) :KS :)

---

### Post by narkulome on 2009-05-03
hmm one moment also:

autostart script: *gksu wifi.sh*
where *wifi.sh* is:
[I]#!/bin/sh
depmod -a
modprobe wl[/I]

Or after reboot the network falls... :(

---

