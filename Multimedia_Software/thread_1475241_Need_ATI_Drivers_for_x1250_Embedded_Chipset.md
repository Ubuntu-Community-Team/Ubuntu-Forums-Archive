---
title: "Need ATI Drivers for x1250 Embedded Chipset"
date: 2010-05-06
forum: Multimedia Software
---

### Post by FlapBags on 2010-05-06
Ok, ATI has a driver listed for Linux x64 for the Radeon x1250 and this  is what happens when you run it, I got the same results with Fedora 12  also.

  Ubuntu runs GREAT on my laptop, but 3D acceleration would be nice, if I  can get this driver, I will be set free of Microsoft almost completely.  Any ideas? Please do not suggest I buy a new laptop, its a Turon X2 and  its powerful enough for me. Thanks!

Acer Extensa 5420  
Turion 64 X-2 TL-58 @1.9ghz
ATI Embedded Mobile Radeon x1250
2gb DDR2 
160gb Toshiba MK series, the ones with bad sectors ;( <-- direct  decendant of the IBM "DeathStar" Series of drives
Atheros Mini PCIx
Marvell GB Ethernet

This is the wonderful surprise I get when I run ATi`s recommended  driver.

root@Ubuntu-acer:~# sh  /home/devadmin/Downloads/ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.zL6f67
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux  Driver-8.593.............................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..........................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:mad:86_64:lib32::none:2.6.32-21-generic;  make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.zL6f67
root@Ubuntu-acer:~#

-------------------------------------------------------------------------

SO, its clear that I have no 3d acceleration, my second display is all garbled like the refresh rates isnt being applied properly, and It would seem some lame generic driver is loaded for my GPU, does anyone have any idea if and when  or where a proper Hardware driver for the x1250 series will be released? 

I hate to go back to Windows, but this is a deal breaker.

---

### Post by Yellow Pasque on 2010-05-06
ATI stopped supporting the X1k chips last year. You either need to run an older distro (like Hardy or Debian Lenny) to use the Catalyst 9-3 drivers or stick with the open-source drivers. Older Catalyst versions don't work with newer Xservers.

Note: You screwed up your install, so see this to revert to stock configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

After you do that, you may be interested in trying the newer open-source 3D drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

