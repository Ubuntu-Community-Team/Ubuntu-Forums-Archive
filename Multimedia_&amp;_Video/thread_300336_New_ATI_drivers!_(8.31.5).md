---
title: "New ATI drivers! (8.31.5)"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by ilbozo on 2006-11-15
Ati released new drivers!
Installed with the same method for 8.30.3 but i dunno if there are significative changes...

---

### Post by ReaderRat on 2006-11-15
> **ilbozo said:**
> **Ati released new drivers!**
Installed with the same method for 8.30.3 but i dunno if there are significative changes...
Where can they be found?

---

### Post by mrfuzzemz on 2006-11-15
Any one happen to know if AIGLX is yet supported? I assume not, but that would be nice.

---

### Post by Melcar on 2006-11-15
Using them right now on my 200M.  FPS went up in glxgears but performance is still worse than in Dapper.

---

### Post by bofphile on 2006-11-15
Same here with my Xpress 200M. If only they could fix the memory issue.

---

### Post by IanW on 2006-11-16
Drivers are [here.]("http://ati.amd.com/support/driver.html")

_Release notes_

Resolved Issues

The following section provide a brief description of resolved issues with the latest version of the AMD Proprietary Linux driver. These include:

    * Setting the display resolution to 400x300 or less no longer results in the mouse pointer not being able to move across the entire desktop. Further details can be found in topic number 733-23732
    * The graphics driver no longer hangs the system shortly after the X Server is started on Red Hat enterprise Linux 3 system running Uniprocessor kernels. Further details can be found in topic number 733-23731
    * Playing a media file under any distribution with X Server 6.9 or greater no longer results in a brief pause or video tearing when resizing the video window or running the mouse pointer over the video player window. Further details can be found in topic number 733-23730
    * Using aticonfig to set the TV format to PAL-COMB-N no longer fails to update the X Server configuration file. Further details can be found in topic number 733-23729 

Known Issues

The following section provides a brief description of known issues associated with the latest version of AMD Proprietary Linux driver. These issues include:

    * Attempting to install the AMD Proprietary Linux driver on distributions that have updated certain 3D components outside of the stock XOrg 6.8.2 may result in the driver not initializing 3D applications properly. Further details can be found in topic number 737-20868
    * Loading the XVideo Extension on 64-bit Xorg 6.9+ systems causes the X Server to segfault on launch with Radeon X1K products. Further details and the workaround can be found in topic number 737-22837
    * A system hang may occur when attempting to resume from hibernation mode. Further details can be found in topic number 737-22059

---

### Post by Onyros on 2006-11-16
I advise people to ALWAYS choose their version of drivers from ATI's site, and not just install the latest drivers available.

I have a Mobility Radeon on my laptop (X700), and blinded by innovation installed the last version, with a bunch of associated problems stemming from that.

Throught their website, found out that the recommended version for the MR X700 is 8.29.6, I'm installing these instead right now.

I had worse performance with these last drivers and had problems coming back from suspension.

---

### Post by IanW on 2006-11-16
> **Onyros said:**
> I advise people to ALWAYS choose their version of drivers from ATI's site, and not just install the latest drivers available.

I agree, that's why I linked to the _start_ of ATI's driver select dialog.

---

### Post by Patskumaster on 2006-11-16
I can't install these new drivers. I try following command **bash ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/edgy** but it not create .deb packages. Anybody help?

---

### Post by Melcar on 2006-11-16
> **Patskumaster said:**
> I can't install these new drivers. I try following command **bash ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/edgy** but it not create .deb packages. Anybody help?

You need to specify the path where the driver is. Ex; **bash ~/Desktop/ati-driver-installer-8.31.5-x86-x86_64.run --builddpkg Ubuntu/edgy**

> **Onyros said:**
> I advise people to ALWAYS choose their version of drivers from ATI's site, and not just install the latest drivers available.

I have a Mobility Radeon on my laptop (X700), and blinded by innovation installed the last version, with a bunch of associated problems stemming from that.

Throught their website, found out that the recommended version for the MR X700 is 8.29.6, I'm installing these instead right now.

I had worse performance with these last drivers and had problems coming back from suspension.

The "recommended" drivers for my 200M are the 8.29 ones but I installed the new ones anyways.  Performance went up (but it's still crappy) and battery life seemed to increase on my laptop:-k .  It really depends on your individual device and the only way to know for certain is to try every single driver version.

---

### Post by Patskumaster on 2006-11-16
> **Melcar said:**
> You need to specify the path where the driver is. Ex; **bash ~/Desktop/ati-driver-installer-8.31.5-x86-x86_64.run --builddpkg Ubuntu/edgy**

Now I get following error...

```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.31.5....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
[: 182: ==: unexpected operator
./packages/Ubuntu/ati-packager.sh: 182: pushd: not found
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
./packages/Ubuntu/ati-packager.sh: 182: popd: not found
Removing temporary directory: fglrx-install

```

---

### Post by Melcar on 2006-11-16
> **Patskumaster said:**
> Now I get following error...

```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.31.5....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
[: 182: ==: unexpected operator
./packages/Ubuntu/ati-packager.sh: 182: pushd: not found
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
./packages/Ubuntu/ati-packager.sh: 182: popd: not found
Removing temporary directory: fglrx-install

```

Is that the correct path of the driver (do you have it on the desktop or is it on another folder?).  Are you typing the exact name of the driver?
This is the guide I follow for all my driver installs (Method 2):
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually")

---

### Post by WalmartSniperLX on 2006-11-16
> =Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.31.5....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
[: 182: ==: unexpected operator
./packages/Ubuntu/ati-packager.sh: 182: pushd: not found
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
./packages/Ubuntu/ati-packager.sh: 182: popd: not found
Removing temporary directory: fglrx-install

put the driver installer in the Home dir and just do it the way you did it w/o the dir path.

It worked for me when I had the same problem. Hope it works for you too.

---

### Post by Patskumaster on 2006-11-17
Thank you, now it works.

Foremost driver package be situated in **ati** directory, but when I move package to my home directory it works!

My english is bad, I hope you understand. ;)

---

### Post by Icarosaurus on 2006-11-23
Why the ati drivers starting form 8.30. ignore my custom modelines??
How can I revert to the 8.28 edgy default?

---

### Post by mrfuzzemz on 2006-11-23
I've upgraded to the new driver, but now there is no direct rendering. I've tried a few things to get it working, but still no good. How might I go back to my old driver to restore the direct rendering I once had?  Thanks so much.

---

### Post by danboy on 2006-12-13
Melcar-

What method did you use to install the 8.31 drivers on your 200m? I havent been able to get them to work since dapper/8.24.

could you post your xorg.conf?

THX

/danboy

---

### Post by mrfuzzemz on 2006-12-13
I've only been able to get direct rendering with the included edgy driver and it is slow (208 fps in glxgears, and HL2 won't fully start with cedega or the latest version of wine.  Cedgega says that it also fails the 3D acceleration test). I've built packages for the latest suggested  driver for my Mobile x1600 and the 8.31.5 driver and installed them.  X starts at the proper resolution, but if I do a ```
fglrxinfo
``` I get info about Mesa where I should be seeing that I have an ATI mobility x1600.  Any ideas?

Thanks a lot.

---

