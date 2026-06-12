---
title: "Slow 3D video with games"
date: 2009-02-19
forum: Multimedia Software
---

### Post by quiteconfused on 2009-02-19
I just replaced Fedora Core 2 (I'd set up a few  years back) with Ubuntu 8.10. Hardware is:
Motheboard is ASUS A7V with 800MHz Duron (with 512MB)
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

The OS installation went smoothly and I really like the OS.  However, one goal was to install a few games, and I've encountered some challenges:
- Planet Penguin is VERY slow and jerky
- Chromium flashed on the screen and disappeared (could not start)
- Tuxcart was VERY slow
- Supertux was VERY slow
- Torcs was VERY slow
Basically many games requiring modest graphics were quite slow.  I am somewhat puzzled because both TuxRacer and Chromium were running fine on Fedora Core 2 on the same hardware.  It's been several years (4?) since I had set these up and really don't recall the specifics.

I first thought this might be related to 3D acceleration not being enabled, but the following seems to indicate it is enabled:
$ glxinfo | less | grep Yes
direct rendering: Yes
$ glxgears
2321 frames in 5.0 seconds = 464.011 FPS
2276 frames in 5.0 seconds = 454.751 FPS
2041 frames in 5.0 seconds = 408.144 FPS
2264 frames in 5.0 seconds = 452.731 FPS
2348 frames in 5.0 seconds = 469.435 FPS
2347 frames in 5.0 seconds = 469.328 FPS
2347 frames in 5.0 seconds = 469.204 FPS

I realize the hardware I'm running on is modest, but it was adequate before I switched to Ubuntu 8.10.  This leads me to believe the performance is either a software configuration issue, or that the software has grown more complex and slower since my prior experience.

Any suggestions as to how I might get some of these games running with useable performance (short of purchasing new hardware) are appreciated?  If that is not likely, feel free to volunteer that opinion too.

This is my first post and I'm not a linux expert, so please go slow ... :-)

---

### Post by Reeman on 2009-02-20
> **quiteconfused said:**
> I just replaced Fedora Core 2 (I'd set up a few  years back) with Ubuntu 8.10. Hardware is:
Motheboard is ASUS A7V with 800MHz Duron (with 512MB)
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

The OS installation went smoothly and I really like the OS.  However, one goal was to install a few games, and I've encountered some challenges:
- Planet Penguin is VERY slow and jerky
- Chromium flashed on the screen and disappeared (could not start)
- Tuxcart was VERY slow
- Supertux was VERY slow
- Torcs was VERY slow
Basically many games requiring modest graphics were quite slow.  I am somewhat puzzled because both TuxRacer and Chromium were running fine on Fedora Core 2 on the same hardware.  It's been several years (4?) since I had set these up and really don't recall the specifics.

I first thought this might be related to 3D acceleration not being enabled, but the following seems to indicate it is enabled:
$ glxinfo | less | grep Yes
direct rendering: Yes
$ glxgears
2321 frames in 5.0 seconds = 464.011 FPS
2276 frames in 5.0 seconds = 454.751 FPS
2041 frames in 5.0 seconds = 408.144 FPS
2264 frames in 5.0 seconds = 452.731 FPS
2348 frames in 5.0 seconds = 469.435 FPS
2347 frames in 5.0 seconds = 469.328 FPS
2347 frames in 5.0 seconds = 469.204 FPS

I realize the hardware I'm running on is modest, but it was adequate before I switched to Ubuntu 8.10.  This leads me to believe the performance is either a software configuration issue, or that the software has grown more complex and slower since my prior experience.

Any suggestions as to how I might get some of these games running with useable performance (short of purchasing new hardware) are appreciated?  If that is not likely, feel free to volunteer that opinion too.

This is my first post and I'm not a linux expert, so please go slow ... :-)
Install the proprietary ATI driver! You have a graphic card which should do it. You can get the driver directly from ATI just make sure you follow the directions and let the installer build the ati module...do not try to let it find an RPM! If you can install the driver with the utility shown here then you will find that the whole process is easy...however if it borks you can always do a #dpkg-reconfigure -phigh xserver-xorg and switch to the vesa driver to get X back again. 

The ubuntu automated install borked on my amd64x2 2700 with a radeon integrated X1250 I found it easier to just follow the instruction at the ATI web site and build my own driver. Now I can run Warsow at 62 fps with absolutely no stutter or sound pops.  Your mileage will vary! Usually the automated restricted driver installs just work for Ubuntu. I assure you the ati proprietary driver is not install by default the way RedHat or Suse does.

Best of Luck](*,)

---

### Post by quiteconfused on 2009-02-20
I did go looking for a proprietary driver.

The ATI web site ([http://ati.amd.com/support/driver.HTML]("http://ati.amd.com/support/driver.HTML")) doesn't appear to support for Radeon 7000/VE.

Absence of proprietary driver support also seems to be confirmed by this wiki -> [http://en.wikipedia.org/wiki/Radeon]("http://en.wikipedia.org/wiki/Radeon")  (see the "Linux" section).

I am still puzzled as to why I got such comparitively better performance with this same hardware with Fedora Core 2.

Any other thoughts on this subject are appreciated ...

---

