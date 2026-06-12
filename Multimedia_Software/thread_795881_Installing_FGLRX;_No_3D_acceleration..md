---
title: "Installing FGLRX; No 3D acceleration."
date: 2008-05-15
forum: Multimedia Software
---

### Post by markekeller on 2008-05-15
I'm attempting to install the fglrx graphics driver.  I've had bad experiences with both Envy and the Restricted Drivers Manager, so I decided to try it manually, following the steps on [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a").  I downloaded the driver from the ATI website, and ran:```
sudo apt-get install dpkg-dev debhelper libstdc++5 dkms
./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/gutsy
sudo dpkg -i fglrx-kernel-source_8.476-0ubuntu1_i386.deb
sudo dpkg -i xorg-driver-fglrx_8.476-0ubuntu1_i386.deb
sudo aticonfig --initial
sudo reboot
```And the computer started up again.  The screen resolution was higher than what I normally use, so I thought it had worked - but I tried running a 3D game, and the framerate was atrocious (worse than when I used the ati driver); obviously no 3D acceleration.  Indeed, upon running fglrxinfo, I got:```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```And while looking through the Xorg log file, I came across the following error:```
EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```Which explains what's wrong, I guess.  I followed the instructions perfectly, though, so why is this happening?

And, more particularly - how can I fix it?

---

### Post by overdrank on 2008-05-15
Hi and I am not currently using a ATI card but what is the model of the card?

---

### Post by markekeller on 2008-05-16
It's a Radeon 9600.  I have gotten fglrx to work before (with different variants of Ubuntu), so I know it's possible on my computer, but I'm not sure what to do about this problem.

---

### Post by overdrank on 2008-05-16
> **markekeller said:**
> It's a Radeon 9600.  I have gotten fglrx to work before (with different variants of Ubuntu), so I know it's possible on my computer, but I'm not sure what to do about this problem.

Hi and I have that model of card but not on a running system at the moment. When I did run Gusty I just used the ati drivers that came with and all work fine. Sorry I could not be of more help.

---

### Post by Gunman1982 on 2008-05-16
It would be interesting to see your xorg.conf ( "/etc/X11/xorg.conf") and which modules are loaded, you can see that if you open a console and type 'cat /proc/modules' (without ' of course)
if that list doesn't show an entry like:
fglrx 1539852 38 - Live 0xf900a000 (P)
than try the following
log off (no need to restart)
press ctrl + alt + F1 
type in your username + password
type in 'sudo killall gdm'
type in 'sudo modprobe fglrx 2>&1 > modprobe_fglrx_err.txt'
type in 'sudo gdm'
log in again
look in your home directory for a file with the name modprobe_fglrx_err.txt and post it here ;)

---

### Post by Ren Höek on 2008-05-17
> **markekeller said:**
> 
[..]
I came across the following error:```
EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```Which explains what's wrong, I guess.  I followed the instructions perfectly, though, so why is this happening?

And, more particularly - how can I fix it?

I had this error too...
If you try
```
$ modprobe -vf fglrx
```
you will probably get something like
```
install /sbin/lrm-video fglrx
```.
The solution is to modify the file "/etc/modprobe.d/lrm-video". Comment out the line with fglrx so it looks like
```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```
and reboot.

Another reason for this error is the use of rt kernel. If this is the case, there seems to be a fix or you can try another kernel...

---

### Post by markekeller on 2008-05-17
Thanks, Ren!  Commenting out that line worked, and now I have 3D acceleration (and the mouse works fine in DOSBox, too, which it didn't with the version of fglrx shipped with Gutsy)!  Oh, and by the way, Gunman1982, I tried generating some error info first, like you suggested, but the outputted text file was blank, for some reason.  :confused:

One problem, yet, though: the graphics driver seems to be kind of unstable or something.  I've had the kernel crash 5 or 6 times already today, mostly while playing 3D games (and I know it was the kernel, because Skinny Elephanting didn't work).  Have you ever experienced that?  Any idea how to prevent it?

---

### Post by Ren Höek on 2008-05-18
> **markekeller said:**
> 
[..]
One problem, yet, though: the graphics driver seems to be kind of unstable or something.  I've had the kernel crash 5 or 6 times already today, mostly while playing 3D games (and I know it was the kernel, because Skinny Elephanting didn't work).  Have you ever experienced that?  Any idea how to prevent it?

Well, the fglrx-driver is sometimes really a little bit sensitive...
I experience crashes with gnome-screensaver (maybe this is also one of your crash reasons...if so, deactivate or change against xscreensaver) and standby.
But if you get the crashes always with the same game, there are possibly some options existing to stop it...
Where do you get the most crashes? Is it always the same game situation? Do you use wine?

---

### Post by markekeller on 2008-05-21
This is kind of an old thread (for this forum), but I guess I'll reply anyway. :)  I haven't had any X or kernel crashes since that first day.  I was playing Blob and Conquer every time it crashed, except I think for one time, when there was nothing 3D open.  On Monday my brother played Alien Arena on it for a couple of hours, with no ill effects, so perhaps it's just something with B&C.  And nope, not Wine. ;)

---

