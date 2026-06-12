---
title: "Broadcom BCM70015 Crystal HD] - Dell inspiron Duo 1090 - Ubuntu 13.04"
date: 2013-07-05
forum: Multimedia Software
---

### Post by SSJ2Son_Gohan on 2013-07-05
Hey folks, 

i will describe the way walked to install the driver for CrystalHD.
i hope it will help in any way...
- i think Broadcom doesnt work, although it is installed correctly ?!?
- sorry for my poor englisch

_Hardware:_
Dell inspiron Duo 1090
Broadcom BCM70015

_OS:_
Ubuntu 13.04
3.8.0-26-generic

_A. Sources:_
[http://www.mythtv.org/wiki/Broadcom_Crystal_HD](http://www.mythtv.org/wiki/Broadcom_Crystal_HD)
[http://www.ubuntuupdates.org/package/core/raring/universe/base/crystalhd-dkms](http://www.ubuntuupdates.org/package/core/raring/universe/base/crystalhd-dkms)
[http://multimedia.cx/eggs/installing-crystalhd-drivers-in-linux/](http://multimedia.cx/eggs/installing-crystalhd-drivers-in-linux/)
[http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu](http://knowledge.evot.biz/documentation/how-to-compile-and-install-the-broadcom-crystal-hd-hardware-decoder-bcm70012-70015-driver-on-ubuntu)
[https://bbs.archlinux.org/viewtopic.php?id=135512](https://bbs.archlinux.org/viewtopic.php?id=135512)
[http://geekparadise.de/2011/04/crystalhd-libcrystalhd-und-gstreamer-plugin-in-ubuntu-kompilieren/](http://geekparadise.de/2011/04/crystalhd-libcrystalhd-und-gstreamer-plugin-in-ubuntu-kompilieren/)
[http://ubuntuforums.org/showthread.php?t=1658635&highlight=crystalhd](http://ubuntuforums.org/showthread.php?t=1658635&highlight=crystalhd)
[http://forum.xbmc.org/showthread.php?tid=70537&page=22](http://forum.xbmc.org/showthread.php?tid=70537&page=22)
[http://ubuntuforums.org/archive/index.php/t-1959705.html](http://ubuntuforums.org/archive/index.php/t-1959705.html)
[https://launchpad.net/ubuntu/raring/+package/crystalhd-dkms](https://launchpad.net/ubuntu/raring/+package/crystalhd-dkms)
[URL="http://www.wetab-community.com/index.php?/topic/19984-ubuntu-1304-installations-how2/"]http://www.wetab-community.com/index.php?/topic/19984-ubuntu-1304-installations-how2/
[COLOR=#222222]
[/COLOR][/URL]- maybe there are som sources with are not listet, because i read it half a year ago, while testing OpenSuSE 12.2 / 12.3-MileStone

[[COLOR=#222222]_1. Install need packages_[/COLOR]]("http://www.wetab-community.com/index.php?/topic/19984-ubuntu-1304-installations-how2/") 

sudo apt-get install checkinstall git-core autoconf build-essential subversion dpkg-dev fakeroot pbuilder build-essential dh-make debhelper devscripts patchutils quilt git-buildpackage pristine-tar git yasm zlib1g-dev zlib-bin libzip-dev libx11-dev libx11-dev libxv-dev vstream-client-dev libgtk2.0-dev libpulse-dev libxxf86dga-dev x11proto-xf86dga-dev git libgstreamermm-0.10-dev libgstreamer0.10-dev automake


sudo apt-get install libpng12-0 libpng3 gstreamer1.0-crystalhd
sudo apt-get install dkms

sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get upgrade 

[U]2. Reboot your system
[/U]
sudo reboot

_3. Install CrystalHD-Packages_
sudo apt-get install crystalhd-dkms firmware-crystalhd


_4. Download and unpack CrystalHD_
[http://www.broadcom.com/support/crystal_hd/](http://www.broadcom.com/support/crystal_hd/)
[http://www.broadcom.com/docs/support/crystalhd/crystalhd_linux_20100703.zip](http://www.broadcom.com/docs/support/crystalhd/crystalhd_linux_20100703.zip)

_5. Copy firmeware to /lib/firmware_

sudo cp /PATH/TO/crystalhd_linux_20100703/crystalhd_07032010/firmware/fwbin/70015/bcm70015fw.bin /lib/firmware/

_6. If crystalhd-dkms not found - if found you can skip _

-Deinstall CrystalHD-Package, only to be sure
sudo modprobe -r crystalhd
sudo apt-get remove crystalhd-dkms

_6.1 Download CrystalHD-DKMS from Launchpad_
[URL="https://launchpad.net/ubuntu/raring/+package/crystalhd-dkms"]
https://launchpad.net/ubuntu/raring/+package/crystalhd-dkms[/URL]
-extract CrystalHD-DKMS package
-edit crystalhd_misc.h

sudo gedit /PATH/TO/crystalhd-dkms_0.0~git20110715.fdd2f19-7_amd64/usr/src/crystalhd-0.0~git20110715.fdd2f19/driver/linux/crystalhd_misc.h

-Change/Comment line: 

#include <asm/system.h> to //#include <asm/system.h>

-save file
-edit crystalhd_lnx.h
 
sudo gedit /PATH/TO/crystalhd-dkms_0.0~git20110715.fdd2f19-7_amd64/usr/src/crystalhd-0.0~git20110715.fdd2f19/driver/linux/crystalhd_lnx.h

-Change/Comment line:

#include <asm/system.h> -> //#include <asm/system.h>

-save file
[U]
6.2 Download Patch[/U] 
[http://www.alexboehm.de/wetab/devinitFix.patch](http://www.alexboehm.de/wetab/devinitFix.patch)

-Insert Patch

cd /PATH/TO/crystalhd-dkms_0.0~git20110715.fdd2f19-7_amd64/usr/src/crystalhd-0.0~git20110715.fdd2f19/
sudo patch -p0  < /data/Websites/CrystalHD/devinitFix/devinitFix.patch

_6.3 Rename downloaded Original-CrystelHD-Package_

_6.4 "ReDeb" the CrystalHD-Package_

cd /PATH/TO/
sudo dpkg -b crystalhd-dkms_0.0~git20110715.fdd2f19-7_amd64

[U]6.4 Install your changed CrystalHD-Package
[/U]
//changed Deb-Package, sorry here it is the same name as original file

sudo dpkg -i /PATH/TO/crystalhd-dkms_0.0~git20110715.fdd2f19-7_amd64.deb 

[U]7. restart your system
[/U]
sudo reboot
sudo modprobe crystalhd


_7.1 Console-Output_

sudo modinfo crystalhd

filename:       /lib/modules/3.8.0-26-generic/updates/dkms/crystalhd.ko
alias:          crystalhd
license:        GPL
description:    Broadcom Crystal HD Decoder Driver
author:         Prasad Bolisetty <prasadb@broadcom.com>
author:         Naren Sankar <nsankar@broadcom.com>
srcversion:     7415D02AE951A7B8B6DB5B2
alias:          pci:v000014E4d00001615sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001612sv*sd*bc*sc*i*
depends:        
vermagic:       3.8.0-26-generic SMP mod_unload modversions


lspci -v

01:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]
    Subsystem: Dell Device 048b
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 90800000 (64-bit, non-prefetchable) [size=64K]
    Memory at 90000000 (64-bit, non-prefetchable) [size=8M]
    Capabilities: <access denied>
    Kernel driver in use: crystalhd


dmesg | grep crys

[    5.175913] Loading crystalhd v3.10.0
[    5.175982] crystalhd 0000:01:00.0: Starting Device:0x1615
[    5.177961] crystalhd 0000:01:00.0: irq 45 for MSI/MSI-X


_8. I did also, because i thought i could reenable with CrystalHD-Indicator_

sudo chown root:users /dev/crystalhd
sudo chmod a+rw /dev/crystalhd


[U]9. Activate CrystalHD
[/U]
[U]9.1 at Start
[/U]sudo echo crystalhd >> /etc/modules
[U]
9.2 after Sleep[/U]
sudo gedit /etc/pm/sleep.d/20-crystalhd

- Insert following lines, but did not work for me:

#!/bin/bash
case "${1}" in
    resume|thaw)
        modprobe -r crystalhd
        modprobe crystalhd && chmod a+rw /dev/crystalhd
;;
esac

_10. Install FlashPlugin_

- i read it will only work till FlashPlayer 10.2 / 10.3
- Chrome: Pepperflash must be disabled

sudo apt-get install adobe-flashplugin
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg

- Insert following lines
EnableLinuxHWVideoDecode=1
nOverrideGPUValidation=true


_11. Things to do..._

_11.1 There is a 20-crystalhd.rules but i dont know where to copy_

sudo cp /PATH/TO/crystalhd_linux_20100703/crystalhd_07032010/driver/linux/20-crystalhd.rules

_11.2 Found this, but it wont work if CrystalHD is recognized_ 

sudo mknod -m 666 /dev/crystalhd c 251 0

---

