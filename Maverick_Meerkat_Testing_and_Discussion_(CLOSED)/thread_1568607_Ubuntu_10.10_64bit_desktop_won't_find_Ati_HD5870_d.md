---
title: "Ubuntu 10.10 64bit desktop won't find Ati HD5870 drivers"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by psychokilla on 2010-09-05
I've installed the beta and as the title says, Ubuntu won't find any drivers for my Ati HD5870 card so I'm stuck with the basic desktop functionality. It makes movies look like sh... 

I tried downloading/installing the Ati drivers from their website and they won't install properly either.

Help please?

Here's what happened...

> *****:~/Downloads$ ./ati-driver-installer-10-8-x86.x86_64.run
Created directory fglrx-install.TSzyvS
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.762........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-19-generic:; make sure that the version is being
correctly set by --iscurrentdistro

=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-19-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.TSzyvS
*****:~/Downloads$ 


---

### Post by Tracy177 on 2010-09-05
i have ati and i have advice for ya

install catalyst from AMD it work for 32 and 64 

and will show you what would you be able to do with fglrx 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4850
OpenGL version string: 3.3.10151 Compatibility Profile Context

aticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Mobility Radeon HD 4850
            Sensor 0: Temperature - 52.00 C


aticonfig --adapter=0 --od-getclocks

Adapter 0 - ATI Mobility Radeon HD 4850
                            Core (MHz)    Memory (MHz)
           Current Clocks :    500           850
             Current Peak :    500           850
  Configurable Peak Range : [500-550]     [850-900]
                 GPU load :    0%


with catalyst youre able to reconfigure everything u want to 


sometimes when you try to install catalys in ubuntu u would need to isntall a few times for example you download it install it reboot and if you start ubuntu again and it boots in low graphic mode reinstall catalyst i had to do it 4 times.

and after u install it to reconfigure xorg type in termianl 


aticonfig --initial --input=/etc/X11/xorg.conf


Linux matrix 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 04:24:28 UTC 2010 i686 GNU/Linux



thats all i tested both open source and catalyst and catalyst is a way better



AND i think you downloaded a wrong catalyst !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


do you have laptop or desktop pc? can u show me the link you got your driver from ?

---

### Post by psychokilla on 2010-09-05
Nope, It was the right version> I managed to fix it after some googling. 

Here's what I did...

> billy@billy-desktop:~/Downloads$ ./ati-driver-installer-10-8-x86.x86_64.run --listpkg
Created directory fglrx-install.s5RKlX
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.762........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
List of generatable packages:

Package Maintainer(s): Aric Cyr <aric.cyr@gmail.com>
                      Mario Limonciello <superm1@gmail.com>
Status: *UNVERIFIED*
Debian Packages:
    Debian/sid
    Debian/unstable
    Debian/etch
    Debian/stable
    Debian/lenny
    Debian/testing
    Debian/experimental

Package Maintainer(s): Niko Mirthes <nmirthes@gmail.com>
                      Michael Larabel <michael@phoronix.com>
Status: *UNVERIFIED*
Fedora Packages:
    Fedora/FC3
    Fedora/FC4
    Fedora/FC5
    Fedora/FC6
    Fedora/F7
    Fedora/F8
    Fedora/F9
    Fedora/F10
    Fedora/RHEL3
    Fedora/RHEL4

Package Maintainer(s): Anssi Hannula <anssi@mandriva.org>
Status: *UNVERIFIED*
Mandriva Packages:
    Mandriva/2007.0
    Mandriva/2007.1
    Mandriva/2008.0
    Mandriva/2008.1
    Mandriva/2009.0
    Mandriva/2009.1
    Mandriva/2010.0
    Mandriva/2010.1

Package Maintainer(s): Bowen Zhu <bwzhu@redflag-linux.com>
Status: *UNVERIFIED*
RedFlag Packages:
    RedFlag/RF50
    RedFlag/RF60sp2
    RedFlag/RF70

Package Maintainer(s): ATI
Status: Verified
RedHat Packages:
    RedHat/RHEL4_64a
    RedHat/RHEL4
    RedHat/RHEL5_64a
    RedHat/RHEL5

Package Maintainer(s): Emanuele Tomasi <tomasi@cli.di.unipi.it>
                      Ezio Ghibaudo <ekxius@gmail.com>
                      Federico Rota <federico.rota01@gmail.com>
Status: *UNVERIFIED*
Slackware Packages:
    Slackware/All
    Slackware/Only_Module
    Slackware/Only_X

Package Maintainer(s): Bob Walmsley <bob@walmsley.com.au>
Status: *UNVERIFIED*
SuSE Packages:
    SuSE/SLE10-IA32
    SuSE/SUSE103-IA32
    SuSE/SUSE110-IA32
    SuSE/SLE10-AMD64
    SuSE/SUSE103-AMD64
    SuSE/SUSE110-AMD64
    SuSE/SLE11-IA32
    SuSE/SUSE111-IA32
    SuSE/SUSE112-IA32
    SuSE/SLE11-AMD64
    SuSE/SUSE111-AMD64
    SuSE/SUSE112-AMD64
    SuSE/SUSE113-IA32
    SuSE/SUSE113-AMD64

Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
                      Alberto Milone <alberto.milone@canonical.com>
Status: *UNVERIFIED*
Ubuntu Packages:
    Ubuntu/gutsy
    Ubuntu/hardy
    Ubuntu/intrepid
    Ubuntu/jaunty
    Ubuntu/karmic
    Ubuntu/lucid
    Ubuntu/source
    Ubuntu/maverick

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch

Removing temporary directory: fglrx-install.s5RKlX


You notice that maverick is in the list, so then you type this in terminal :

> ./ati-driver-installer-10-8-x86.x86_64.run --buildpkg Ubuntu/maverick

Which makes the installer build a version for you and spit out a bunch of deb files which you just use to install.

---

### Post by Tracy177 on 2010-09-05
> **psychokilla said:**
> Nope, It was the right version> I managed to fix it after some googling. 

Here's what I did...



You notice that maverick is in the list, so then you type this in terminal :



Which makes the installer build a version for you and spit out a bunch of deb files which you just use to install.



or you can just click auto

---

### Post by chillyperson23 on 2010-09-18
Auto fails saying that the distro is unsupported.  I'm going to try out the other method soon.

---

### Post by frunns on 2010-09-20
> **Tracy177 said:**
> or you can just click auto

Didn't even bother to read the first post, did you?

Trying this out now, hoping it works! :)

---

### Post by AVeryLongNickname on 2010-09-20
Hey!

I tried this with the catalyst 10.09 package from ati.com. I got no errors during install, and everything seemed to be ok, untill i restarted the computer.. then it crashed.. couldnt start gnome, so all I got was a terminal.. had to run

sudo apt-get remove fglrx

 to get gnome back..

Any ideas why? :s

---

### Post by Iowan on 2010-09-20
Moved to Maverick Meerkat Testing and Discussion

---

### Post by mendred on 2010-09-29
the reason you may be facing crashes with the driver

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

I have faced the same issue and am waiting for the hotfix to be generally available..currently it cant be downloaded.

---

### Post by cariboo on 2010-09-29
I don't have an ATI card, but I clicked the link, and the hotfix is downloading as I type.

---

### Post by Botruckle on 2010-09-29
The hotfix worked for me. I was getting errors with the video driver after the latest Ubuntu updates. The hotfix cured the issues. Here's the link again:
[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

---

### Post by pepigno75 on 2010-10-02
i try hotfix but same problem, >;make sure that the version is being

```

sudo chmod +x ati-driver-installer-8.771.2-x86.x86_64
sudo ./ati-driver-installer-8.771.2-x86.x86_64

```

first i stop gdm service.


ubuntu 10.10 RC and ati radeon hd5650

---

### Post by rajeev1204 on 2010-10-02
AMD site does not have drivers for maverick as far as i know .Catalyst 10.9 wont work with maverick due to no xserver 1.9 support.

Install the software from hardware drivers , it was just released with the Release candidate 10.10.

---

