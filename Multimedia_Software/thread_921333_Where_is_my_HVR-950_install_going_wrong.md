---
title: "Where is my HVR-950 install going wrong?"
date: 2008-09-16
forum: Multimedia Software
---

### Post by jcoles on 2008-09-16
I have followed the instructions at [http://u32.net/MythTV/WinTV-HVR-950/index.html](http://u32.net/MythTV/WinTV-HVR-950/index.html) several times with no success. I never get the dmesg logs about "tveeprom 2-0050". What I get is this:

[ 1637.831551] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 1637.968745] usb 5-2: configuration #1 chosen from 1 choice
[ 1637.976098] usb 5-2: can't set config #1, error -71

Perhaps the compilation is actually failing at some point. It's hard to tell. I get the following message at the beginning of the "make all":

SOC_CAMERA: Requires at least kernel 2.6.25
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.25
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.25
VIDEO_PXA27x: Requires at least kernel 2.6.26

Is this relevant to the HVR-950? The package has drivers for many devices.

Does this completion of the compile indicate success?:

make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
./scripts/rmmod.pl check
found 261 modules
make[1]: Leaving directory `/home/jcoles/Download/HVR-950/v4l-dvb-e5ca4534b543/v4l'

The make install output includes:
	video/em28xx/: em28xx-dvb.ko em28xx.ko 
	video/au0828/: au0828.ko 
And au8522.ko is listed amongst the dvb/frontends/.

Any ideas why the device remains unrecognized and unusable?

---

### Post by db260179 on 2008-09-16
Head yourself over to [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
and
[http://linuxtv.org/repo/](http://linuxtv.org/repo/)

Follow the guides

> **jcoles said:**
> I have followed the instructions at [http://u32.net/MythTV/WinTV-HVR-950/index.html](http://u32.net/MythTV/WinTV-HVR-950/index.html) several times with no success. I never get the dmesg logs about "tveeprom 2-0050". What I get is this:

[ 1637.831551] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 1637.968745] usb 5-2: configuration #1 chosen from 1 choice
[ 1637.976098] usb 5-2: can't set config #1, error -71

Perhaps the compilation is actually failing at some point. It's hard to tell. I get the following message at the beginning of the "make all":

SOC_CAMERA: Requires at least kernel 2.6.25
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.25
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.25
VIDEO_PXA27x: Requires at least kernel 2.6.26

Is this relevant to the HVR-950? The package has drivers for many devices.

Does this completion of the compile indicate success?:

make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
./scripts/rmmod.pl check
found 261 modules
make[1]: Leaving directory `/home/jcoles/Download/HVR-950/v4l-dvb-e5ca4534b543/v4l'

The make install output includes:
	video/em28xx/: em28xx-dvb.ko em28xx.ko 
	video/au0828/: au0828.ko 
And au8522.ko is listed amongst the dvb/frontends/.

Any ideas why the device remains unrecognized and unusable?

---

### Post by jcoles on 2008-09-16
I would have preferred answers to the questions I asked, but thanks for links to yet more sets of instructions. One day, I might find one that works.

The LinuxTV.org site looks good, but I am already at an impasse with their instructions. The command "hg clone http://linuxtv.org/hg/v4l-dvb" returns "abort: error: Name or service not known". So, it must be incorrect in some way. Looks like these instructions were not tested. 

The URL [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) leads to some list of changes, not to the package. Fortunately, a tarball can be downloaded from that page. (So what was all that guff about needing Mercurial?)

The downloaded tarball is named the same as the one I compiled before. The v4l-apps tarball was called tips.tar.gz in another set of instructions. Nothing is said about compiling it, but I tried that too. As the instructions refer to "v4l-dvb" without the long hex number on the end, I renamed the extracted directory. I did the same to v4l-apps.

After making and installing, I get the same error messages as before. 

I don't mean to be unappreciative. Thanks for pointing me to LinuxTV.org. Perhaps I can follow up with them. I am not a software developer. As I said before, the messages the compiler spews do not clearly indicate success or failure to me. Can you see some "obvious" unstated step that I am missing?

---

