---
title: "fglrx with xserver 1.8 (in progress)"
date: 2010-06-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-06-15
*Updated for 10.9 and xorg-server 1.9*

I'm not updating this post any more as Maverick has moved to xorg-server 1.9. My thread for fglrx and 1.9: [http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

*Updated for 10.7*

It appears that with xserver-xorg 1.8.1.902-0ubuntu1 fglrx works fine. Either build a patched driver package following the steps below or try the X-Swat PPA.

If you want the latest version of Catalyst (10.7) and don't want to wait for x-swat, then you can create debs directly from the ATi installer:

1) Download ati-driver-installer-10-7-x86.x86_64.run from ATi ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx))

You have a choice; either build .debs then install them so you have a copy, or let the installer build and install them directly. (Extraction and manual patching is unnecessary now - they've fixed it! Well done ATi!)

For .debs to save:
2) $ sh ./ati-driver-installer-10-7-x86.x86_64.run --buildpkg
3) $ sudo dpkg -i *.deb

For direct installation of .debs:
2) $ sh ./ati-driver-installer-10-7-x86.x86_64.run



***

Old manual patching for 10.6:

1) Download ati-driver-installer-10-6-x86.x86_64.run from ATi.
2) Run $ sh ./ati-driver-installer-10-6-x86.x86_64.run --extract ~/temp/ati
3) Enter ati/common/lib/modules/fglrx/build_mod and edit kcl_wait.c, and below "#include <linux/sched.h>" add the lines:

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,34)
#include <linux/slab.h>
#endif

4) In ~/temp/ati run $ ./ati-installer.sh 8.741 Ubuntu/maverick

This will generate all necessary .debs and put them in ~/temp/

***

Older:
Having patched X to report at 1.7.5 I can't comment on whether 10.6 works with 1.8 or not. However, the steps below will install fglrx as a module on any kernel.

***

Original content:
Hello. I'm starting this thread to put some information together about getting fglrx to build against xserver 1.8 (which I just installed and therefore killed my hardware graphics acceleration).

So far I've built an Ubuntu deb from the ATi installer using an adapted configuration for Maverick (using the patches I submitted from Arch) and now have debs that install beautifully - but which don't let X start.

[s]This is annoying, as every module is built against 1.8 except fglrx.so which appears to be stubbornly staying as built against 1.7, despite my best urging (and telling it to build against x750, Xorg 7.5 which is I think xserver 1.8. This might not make any difference? ).[/s]. 

OK, so 10.5 doesn't support xserver 1.8 (1.7 is Xorg 7.5 though[s], so 1.8 is 7.6? [http://www.x.org/wiki/Releases/7.5](http://www.x.org/wiki/Releases/7.5)[/s] ). It's the same Xorg version so there should be a way of getting this to work, though I'm starting to think that fglrx_drv.so is a binary blob that doesn't change - just different versions get installed depending on the version of X.

```

[    32.229] (II) LoadModule: "fglrx"
[    32.229] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    32.386] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    32.386] 	compiled for 1.7.1, module version = 8.73.3
[    32.386] 	Module class: X.Org Video Driver
[    32.386] [atiddxSetup] X version mismatch - detected X.org 7.1.1.901, required X.org 7.5.1.0
[    32.386] (II) UnloadModule: "fglrx"
[    32.386] (II) Unloading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    32.386] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)
[    32.386] (EE) No drivers available.
```

Edit history:
Update for Catalyst 10.7. Really simple now...
Update for xserver-xorg 1.8.1.902-0ubuntu1
Updated for new Catalyst 10.6

---

### Post by jfernyhough on 2010-06-15
Just out of interest I though I'd try building the Ubuntu/lucid config which is against Xorg 7.4. Installing now.

--edit. Nope, same result.

--edit 2

Apparently the driver works fine on 1.8 but this requires patching X to present itself as an earlier version. I'm not touching that at the moment.

---

### Post by mrl586 on 2010-06-15
You can rebuild xorg-server using [this guide]("http://forum.ubuntu-fi.org/index.php?topic=33385.msg266408#msg266408").

---

### Post by jfernyhough on 2010-06-16
Bah...
```
j@arrandale:~/src/xorg$ sudo apt-get build-dep xorg-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-Depends dependency for xorg-server cannot be satisfied because no available versions of package xutils-dev can satisfy version requirements

```

---

### Post by mrl586 on 2010-06-16
What command 'sudo apt-cache policy xutils-dev' says?

---

### Post by jfernyhough on 2010-06-16
```
xutils-dev:
  Installed: (none)
  Candidate: 1:7.5+2
  Version table:
     1:7.5+3 0
        400 http://archive.ubuntu.com/ubuntu/ maverick/main Packages

```

I wonder if I were to use X-Crack; but that really doesn't appeal. :D

--edit 
Hmph. I can install xutils-dev manually; no dependency errors. $ sudo aptitude build-dep xorg-server seems to be the way forward.

---

### Post by jfernyhough on 2010-06-16
OK, to patch xorg-server (which is probably a really bad idea, but hey, if they are doing it on Arch and Gentoo :D).

$ mkdir ~/src/xorg
$ cd ~/src/xorg
$ sudo aptitude build-dep xorg-server
$ apt-get source xorg-server
$ cd xorg-server-1.8.1.901-1ubuntu1
$ nano configure.ac
(find (^W) '[xorg-server], 1.8.1.901,' and replace with '[xorg-server], 1.7.5.1,')
$ dch -i
(add something, e.g. version number hack. Make sure to have a number at the end or the version number line otherwise the build process will fail *at the end* -.-)
$ debuild -uc -us
(may throw up missing deps, install them manually, I had libgpg-dev or similar, then try again)

That should be that. Install the resulting .debs and hope for the best. Mine are building as I type.

---

### Post by jfernyhough on 2010-06-16
Built and installed alongside my fglrx packages. Let's see how this plays out.

--edit
OK, it would have helped if I had actually saved configure.ac after editing it... (and then heeded the initramfs warning. Yayz for a Live USB and chroot!)

---

### Post by jfernyhough on 2010-06-16
Woohoo! It worked!

---

### Post by jfernyhough on 2010-06-17
New drivers out today. Typical. Just after I got it working...

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.30&lang=us&rev=10.6&ostype=Linux%20x86_64](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.30&lang=us&rev=10.6&ostype=Linux%20x86_64)

---

### Post by jfernyhough on 2010-06-17
OK, got 10.6 working. Edited op.

---

### Post by aviramof on 2010-06-17
> **jfernyhough said:**
> New drivers out today. Typical. Just after I got it working...

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.30&lang=us&rev=10.6&ostype=Linux%20x86_64](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.30&lang=us&rev=10.6&ostype=Linux%20x86_64)

The new driver doesn't support xorg 1.8 so how did you get it to work?

---

### Post by alphacrucis2 on 2010-06-18
> **aviramof said:**
> The new driver doesn't support xorg 1.8 so how did you get it to work?

He already explained. He patched xorg 1.8 to fool fglrx.

---

### Post by aviramof on 2010-06-18
Maybe i am a bit confuse here but i see that i have xorg 1.75 and xserver 1.8 so why can't fglrx work with that?

---

### Post by alphacrucis2 on 2010-06-18
> **aviramof said:**
> Maybe i am a bit confuse here but i see that i have xorg 1.75 and xserver 1.8 so why can't fglrx work with that?

He patched xorg-server. See post #7 in this thread

---

### Post by jfernyhough on 2010-06-23
Hmm... with the last X updates (to version 2:1.8.1.902-0ubuntu1) it appears that fglrx works without having to patch.

Did the devs patch the version number? (that was a no-go according to one bug report response) The Catalyst driver definitely hasn't changed.

---

### Post by aviramof on 2010-06-23
[QUOTE=jfernyhough;9501307]Hmm... with the last X updates (to version 2:1.8.1.902-0ubuntu1) it appears that fglrx works without having to patch.

Is there a ppa address for this version?

---

### Post by jfernyhough on 2010-06-24
The update came through in Main.

```
xorg-server (2:1.8.1.902-0ubuntu1) maverick; urgency=low

 * Merge from (unreleased) Debian experimental.  Remaining changes:
   - rules, control:
     + Disable SELinux, libaudit-dev is not in main yet (LP 406226).
       Drop libaudit-dev from build-deps.
   - rules: Enable xcsecurity (LP 247537).
   - local/xvfb-run*: Add correct docs about error codes (LP 328205)
   - rules: Add --with-extra-module-dir to support GL alternatives.
   - control: Xvfb depends on xauth, x11-xkb-utils. (LP 500102)
   - rules, local/64-xorg-xkb.rules: Don't use keyboard-configuration
     until it's available.
   - control: Update some versioned Breaks for Ubuntu versions.
   - debian/patches:
     + 100_rethrow_signals.patch:
       When aborting, re-raise signals for apport
     + 109_fix-swcursor-crash.patch:
       Avoid dereferencing null pointer while reloading cursors during
       resume. (LP 371405)
     + 111_armel-drv-fallbacks.patch:
       Add support for armel driver fallbacks.
     + 121_only_switch_vt_when_active.diff:
       Add a check to prevent the X server from changing the VT when killing
       GDM from the console.
     + 122_xext_fix_card32_overflow_in_xauth.patch:
       Fix server crash when “xauth generate” is called with large timeout.
     + 157_check_null_modes.patch, 162_null_crtc_in_rotation.patch,
       166_nullptr_xinerama_keyrepeat.patch, 167_nullptr_xisbread.patch
       169_mipointer_nullptr_checks.patch,
       172_cwgetbackingpicture_nullptr_check.patch:
       Fix various segfaults in xserver by checking pointers for NULL
       values before dereferencing them.
     + 165_man_xorg_conf_no_device_ident.patch
       Correct man page
     + 168_glibc_trace_to_stderr.patch:
       Report abort traces to stderr instead of terminal
     + 184_virtual_devices_autodetect.patch:
       Use vesa for qemu device, which is not supported by cirrus
     + 187_edid_quirk_hp_nc8430.patch:
       Quirk for another LPL monitor (LP 380009)
     + 188_default_primary_to_first_busid.patch:
       Pick the first device and carry on (LP 459512)
     + 189_xserver_1.5.0_bg_none_root.patch:
       Create a root window with no background.
     + 190_cache-xkbcomp_output_for_fast_start_up.patch:
       Cache keyboard settings.
     + 191-Xorg-add-an-extra-module-path.patch:
       Add support for the alternatives module path.
     + 196_xvfb-fbscreeninit-handling.patch, 197_xvfb-randr.patch:
       Adds xrandr support to xvfb. (LP 516123)
     + 198_nohwaccess.patch:
       Adds a -nohwaccess argument to make X not access the hardware
       ports directly.
     + 200_randr-null.patch:
       Clarify a pointer initialization.
 * Update changelog entries for previously unreleased Debian 1.8.1.901-1

xorg-server (2:1.8.1.902-1) UNRELEASED; urgency=low

 [ Julien Cristau ]
 * Install the upstream changelog in xserver-common, instead of duplicating
   its 1MB in all other packages.

 [ Christopher James Halse Rogers ]
 * New upstream RC
   - A number of DRI2 fixes.
   - Fix for hanging OpenGL clients with multiple heads.
 * 17-fix-DRI2-segfault-when-clientGone.diff:
   - Pick up fix from https://bugs.freedesktop.org/show_bug.cgi?id=27497 to
     fix server crash in DRI2SwapEvent handling (LP: #595182).

Date: Wed, 23 Jun 2010 11:19:49 +1000
Changed-By: Christopher James Halse Rogers <raof@ubuntu.com>
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Signed-By: Luke Yelavich <luke.yelavich@canonical.com>
https://launchpad.net/ubuntu/maverick/+source/xorg-server/2:1.8.1.902-0ubuntu1
```
But for reference here is the X-Swat ppa address: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by aviramof on 2010-06-24
I don't see this update in main and when i add the  X-Swat ppa all i get is fglrx                  2:8.741-0ubuntu0sarvatt2 in fact i can't find 2:1.8.1.902-0ubuntu1 in synaptic at all.

Update:
i installed the                  2:8.741-0ubuntu0sarvatt2 from jockey and it appear to work but compiz doesn't work and there is no smooth scrolling in firefox.

FIXED it with 
sudo aticonfig --initial

But there is some delay in the browser whille surfing.

---

### Post by aviramof on 2010-06-25
I have one problem with this driver and that that the mouse slightly freeze at times meaning he's not running completly smooth 
on the screen but on the other hand plymouth is finally working well meaning i have an ubuntu logo at startup he's not as sleek as with 
xorg and he's slightly bigger but it look much better.:)

---

### Post by PGHammer on 2010-07-11
> **aviramof said:**
> I have one problem with this driver and that that the mouse slightly freeze at times meaning he's not running completly smooth 
on the screen but on the other hand plymouth is finally working well meaning i have an ubuntu logo at startup he's not as sleek as with 
xorg and he's slightly bigger but it look much better.:)

I have a complete set of patched .deb files (built against alpha 2 of Maverick x64); is there anywhere I can submit them?  (I'm running them myself, and they do install/work correctly.)

---

### Post by aviramof on 2010-07-11
Maybe try to contact the owner of the x-swat ppa by email.

---

### Post by ppp0 on 2010-07-27
> **jfernyhough said:**
> OK, to patch xorg-server (which is probably a really bad idea, but hey, if they are doing it on Arch and Gentoo :D).

$ mkdir ~/src/xorg
$ cd ~/src/xorg
$ sudo aptitude build-dep xorg-server
$ apt-get source xorg-server
$ cd xorg-server-1.8.1.901-1ubuntu1
$ nano configure.ac
(find (^W) '[xorg-server], 1.8.1.901,' and replace with '[xorg-server], 1.7.5.1,')
$ dch -i
(add something, e.g. version number hack. Make sure to have a number at the end or the version number line otherwise the build process will fail *at the end* -.-)
$ debuild -uc -us
(may throw up missing deps, install them manually, I had libgpg-dev or similar, then try again)

That should be that. Install the resulting .debs and hope for the best. Mine are building as I type.

when $: sudo aptitude build-dep xorg-server
Unable to find the source package for "xorg-server".

---

### Post by ppp0 on 2010-07-27
> **ppp0 said:**
> when $: sudo aptitude build-dep xorg-server
Unable to find the source package for "xorg-server".
ok. But my xorg version is 1.7.6 with fglrx

---

### Post by rajeev1204 on 2010-07-27
> **ppp0 said:**
> ok. But my xorg version is 1.7.6 with fglrx


Hi, if you want to get fglrx running , just install it from the xswat ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

This will get it working real nice .No need for any compklicated stuff.




rajeev

---

### Post by jfernyhough on 2010-07-27
> **ppp0 said:**
> when $: sudo aptitude build-dep xorg-server
Unable to find the source package for "xorg-server".

Do you have a source line (deb-src) in your /etc/apt/sources.list?

But as has been said, just use the x-swat PPA with the current version of X. It works fine without any patching.

---

### Post by jfernyhough on 2010-07-27
Ooh, 10.7 has just been released! Downloading now and will try the custom .deb method.

--edit
Downloaded. Looks like it's going to be very easy now as the previously needed patching has been taken care of by ATi.

---

### Post by rajeev1204 on 2010-07-27
> **jfernyhough said:**
> Ooh, 10.7 has just been released! Downloading now and will try the custom .deb method.

--edit
Downloaded. Looks like it's going to be very easy now as the previously needed patching has been taken care of by ATi.


Really? No patching ? where is that written ?
ANyway i just downloaded 10.7, lets see how it goes.

Wow, definitely patched to install on any xserver version it seems !

---

### Post by rajeev1204 on 2010-07-27
OK installed , and working fine as of now.

---

### Post by alienexplorers on 2010-07-28
I have been trying to get fglrx up and running for about a week.  Followed your lead and now the fglrx driver is working great.  Thanks all.

---

### Post by rajeev1204 on 2010-07-28
> **alienexplorers said:**
> I have been trying to get fglrx up and running for about a week.  Followed your lead and now the fglrx driver is working great.  Thanks all.


If you used the xswat ppa , it will install the 10.6 driver , but withe the latest version 10.7, you can directly install the driver on your system.

Works fine,has some small issues though with black windows .

Latest update: No reinstallation required after latest kernel update. That's nice.

---

### Post by pr0llux on 2010-09-15
Anybody tried with Catalyst 10.9?

---

### Post by andrek on 2010-09-16
> **pr0llux said:**
> Anybody tried with Catalyst 10.9?
Yes, it doesn't work. Let's hope for fglrx 10.10.

According to some guys from phoronix,
> there are allready a beta 10.10 with xserver 1.9 support and there is a 10.11 beta. 
in 20 days amd will push a 10.10 catalyst into the ubuntu 10.10 repo .


---

### Post by jfernyhough on 2010-09-16
Just to clarify, 10.9 works fine with xorg-server 1.8 (Lucid, early Maverick), but not with 1.9 (current Maverick).

I'd take what someone says on Phoronix with a pinch of salt, as they also said that Catalyst 10.7 would work with server 1.9 (it didn't, obviously).

---

### Post by aviramof on 2010-09-17
> **jfernyhough said:**
> Just to clarify, 10.9 works fine with xorg-server 1.8 (Lucid, early Maverick), but not with 1.9 (current Maverick).
 
I'd take what someone says on Phoronix with a pinch of salt, as they also said that Catalyst 10.7 would work with server 1.9 (it didn't, obviously).
 
I'm really hopping that what Phoronix are saying is true because at the moment for me at least ubuntu without fglrx is not realy ubuntu it is just a plain os for me.

---

