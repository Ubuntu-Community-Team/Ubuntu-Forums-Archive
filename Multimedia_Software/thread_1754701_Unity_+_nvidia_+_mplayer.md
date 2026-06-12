---
title: "Unity + nvidia + mplayer"
date: 2011-05-10
forum: Multimedia Software
---

### Post by gid on 2011-05-10
Ok, I have had this problem with this machine for a while, but only become a problem since upgrading to Natty since the unity interface is kind nice and would like to use it.

Awhile back I noticed if I used compiz with effects enable mplayer would never work properly going full screen.  Without desktop effects, mplayer works great, fullscreen resizing, etc.   I was kind of hoping this upgrade would fix it, but alas, no.

With Unity enabled, resizing or going fullscreen with mplayer results in the video stream being stopped and errors being spewed in the console (I can still hear audio):
X11 error: BadAlloc (insufficient resources for operation)0.7% 6 0 97% 
X11 error: BadAlloc (insufficient resources for operation)0.7% 6 0 96% 
X11 error: BadAlloc (insufficient resources for operation)0.7% 6 0 96%


I've tried the version of mplayer in natty, and then using the one available from medibuntu as well with no luck.  I've also tried using sdl, xv.  It starts out playing fine, but if I resize the video, it freezes and spits out the above error.

The gl and gl2 VO are very slow, as is glxgears, but I do have the proprietary nvidia driver installed and activated.  The "additional drivers" app shows it's active, but not in use, which according to google and people on other forums, this is a bug, but now I'm starting to wonder.

gnome-mplayer and smplayer also do not work properly when resized.

Any idea of what's causing this or where to start looking or trying?  I'd really like to use the unity interface if at all possible.


-----

root@pimpbot:~# dpkg --list |egrep  '(nvidia|mplayer)'
ii  gnome-mplayer                         1.0.2-0ubuntu1                             A GTK+ interface for MPlayer
ii  mplayer                               2:1.0~rc4.dfsg1-1ubuntu3+medibuntu1        movie player for Unix-like systems
ii  nvidia-173                            173.14.30-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver
ii  smplayer                              0.6.9-1                                    complete front-end for MPlayer
ii  smplayer-themes                       0.1.20+dfsg-1                              complete front-end for MPlayer - icon themes
ii  smplayer-translations                 0.6.9-1                                    complete front-end for MPlayer - translation files

root@pimpbot:~# lspci |grep NV
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

root@pimpbot:~# cat /proc/cpuinfo |grep 'model name'
model name	: AMD Athlon(tm) 64 Processor 3400+

---

### Post by ksian on 2011-10-19
I am in the same situation. Does anybody has any ideas?

---

### Post by BicyclerBoy on 2011-10-19
Compiz composite settings manager (ccsm).

composite & opengl must be enabled..
select composite tab
tick un-redirect full screen output
tick/set refresh rate detect (does not work properly with twinview)

select workarounds tab
tick legacy full screen support.

The best solution to video playback would be getting rid of Unity/compiz.
AFAIU The problem is caused by compiz (blitter) interfering with VDPAU or openGL video overlay.

The OPs video card is very slow & has no VDPAU. People with old marginal video cards seem to have more problems with compiz. A replacement like a GT430 would be huge improvement.

---

