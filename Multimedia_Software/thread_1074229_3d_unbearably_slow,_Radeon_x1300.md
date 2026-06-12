---
title: "3d unbearably slow, Radeon x1300"
date: 2009-02-19
forum: Multimedia Software
---

### Post by IsmAvatar on 2009-02-19
I have an ATI Radeon x1300 graphics card which worked wonderfully under windows, I was able to play Halo with all the neat effects turned on, etc.

Now that I've switched over to Ubuntu, and am using the non-proprietary driver for it, anything 3d has slowed to an unberable crawl, usually less than 1 fps if it fills up most of the screen. If it's small, for example, glxgears in its default size, and most of the screensaver previews, it runs great. glxgears at default size runs over 100fps. Resize to fullscreen, and the fps drops to 10, and screensavers seem to drop to 1 fps.

I'm really hopeful that there's something I can do to fix this without resorting to the proprietary driver (which I wasn't able to get working anyways, not to mention if I wanted to go proprietary, I'd just return to Windows). Don't make me pick between Linux and 3d, because I'll pick the latter.

-IsmAvatar

---

### Post by Yellow Pasque on 2009-02-19
Sorry to burst your bubble, but the proprietary ATI driver is the way to go for the best 3D performance. I don't like it either, which is why I don't use it.

> Don't make me pick between Linux and 3d, because I'll pick the latter.
Pick whatever works for you. You can dual-boot if you like Linux as a working environment and Windows as a gaming environmnet. This is not uncommon.

---

### Post by IsmAvatar on 2009-02-19
In which case, I'll need help getting the proprietary driver working. I've installed fglrx, and checked up on System > Administration > Hardware Drivers, and it says the proprietary ATI driver is activated and currently in use. However, something is clearly amiss here because running glxgears in fullscreen, I am only able to get 10 fps, and 3d screensavers don't even show up (I get a white screen).

I followed the instructions on this page: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)
but got stuck when it said "Create .deb packages:", replacing "dapper" with "intrepid" and "26.18" with "27.10"


$ chmod +x ati-driver-installer-8.26.18-x86.run
$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/intrepid
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10........
  <lots of dots here>
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/intrepid
Requested package is not supported.
Removing temporary directory: fglrx-install
$

---

### Post by Yellow Pasque on 2009-02-19
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by IsmAvatar on 2009-02-19
Yay, thank you.

---

### Post by Reeman on 2009-02-19
> **IsmAvatar said:**
> In which case, I'll need help getting the proprietary driver working. I've installed fglrx, and checked up on System > Administration > Hardware Drivers, and it says the proprietary ATI driver is activated and currently in use. However, something is clearly amiss here because running glxgears in fullscreen, I am only able to get 10 fps, and 3d screensavers don't even show up (I get a white screen).

I followed the instructions on this page: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)
but got stuck when it said "Create .deb packages:", replacing "dapper" with "intrepid" and "26.18" with "27.10"


$ chmod +x ati-driver-installer-8.26.18-x86.run
$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/intrepid
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10........
  <lots of dots here>
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/intrepid
Requested package is not supported.
Removing temporary directory: fglrx-install
$


AAARGF use the driver from the [[COLOR="RoyalBlue"]_ATI_[/COLOR]]("http://ati.amd.com/support/driver.HTML") web site it works fine! The precompiled Ubuntu stuff borked me twice with an integrated Radeon X1250...it will not happen again. 

After you **$sudo sh ati-driver-installer-9-1-x86.86_64.run** (which is the latest for your card) let the auto install do its thing instead of looking for a precompiled package as the packages available are only RPMs. You only need the kernel headers install for the installer to work...much more sensible than N-VIdia and you run the installer in X (there is a self explanatory gui).... Just remember to get it cooking you have to let it rewrite /etc/X11/xorg.config you do this with the command "**$sudo aticonfig --initial -f**" .....all of this can be done in the current X session. The next time you startx you will have openGL to the abilities of your card. 

Remember also if you have an true 64 ubuntu install all of the lib32 libraries will need to be in place for the ati installer to work...it says this in the ati docs for the radeon graphics installer.

It is a shame that the only way to get non emulated glx is to use openGL which in reality is closed but we unfortunate   Linux peons just have to put up with the proprietary crap.



Best of luck

---

### Post by IsmAvatar on 2009-02-20
Thanks for responding, but Temüjin got me squared away with the guide he posted, which worked wonders, and I think did what you said. I'm still pretty new to linux, so a lot of what you said is greek to me, but following the guide got me up and running just fine, with glxgears running at anywhere from 100 to 1600 fps (with flickering, but that's probably because it doesn't wait for vertical sync or limit its fps). Also, it appears I have compiz, because all of a sudden X started giving me fancy features like fading tooltips, animated windows, etc.
So I'm pretty sure this problem is resolved. Thanks again, Temüjin especially for pointing out that guide.

---

