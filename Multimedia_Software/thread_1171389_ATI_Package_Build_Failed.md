---
title: "ATI Package Build Failed"
date: 2009-05-27
forum: Multimedia Software
---

### Post by RobOrr on 2009-05-27
I downloaded the Catalyst 9.3 Drivers today (I use a Radeon X700 - now classed as legacy so no 9.4 or Jaunty for me)

- upon attempting to build the ubuntu/intrepid package as per instructed, I got this error pop up in the build stage:

#the line that failed
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
#the error message
dpkg-shlibdeps: failure: couldn't find library libGL.so.1 needed by debian/xorg-driver-fglrx/usr/sbin/atieventsd (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.Y25850

Could anyone help me with this?

EDIT 
To further add to my rage, it appears that attempting this driver update has shafted my current *working* driver setup for the card. upon restarting, a BSOD appeared and I'm now in safe mode. Hardware drivers cannot deactivate my supposed working ATI proprietary drivers as my xorg.conf is now invalid. I hate ATI. fixed this secondary problem by reinstalling the synaptic packages associated with fglrx.

---

### Post by deriamis on 2009-05-27
To get your X server working again, try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should restore your xorg.conf file for you. Just answer the questions appropriately.

As for the ATI drivers, you might want to check out the radeonhd ones. I don't know if they will work for you, but remember to remove xserver-xorg-video-ati before you do it.

---

### Post by RobOrr on 2009-05-28
Solved problem - two of the dependencies (only listed in the installation instructions) had to be reinstalled for no apparent reason. Once done, allowed me to build the intrepid packages normally and from there install them.

---

### Post by AronVanAmmers on 2011-10-24
Thanks, this thread helped me with the exact same problem on Maverick.

Solved by reinstalling the [dependencies listed in the instruction]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Before_you_start"):
```
$ sudo aptitude reinstall build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```

After that the ATI proprietory driver package built beautifully again:
```
$ sudo ./ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/maverick
```

---

