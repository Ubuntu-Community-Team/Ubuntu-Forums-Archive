---
title: "video card, sleep, no output, won't wake"
date: 2010-11-19
forum: Multimedia Software
---

### Post by kobkob on 2010-11-19
Hi Gang,

First of all, I'm sorry if this has already been discussed in another thread, if so, please point me there.  I've tried searching but have had trouble finding anything.  Also, I don't suspect this will be quick problem to fix as it is intermittent.

Seldom, actually very seldom, just a few times a year, my screen will not come out of sleep mode.  Oddly enough, it will come out of sleep mode when I use the keyboard shortcut to change desktops (ctrl-alt-arrow).  As soon as I release the shortcut keys, my monitor goes back to sleep, i.e., "entering power save mode".  As long as I keep pressing the shortcut keys, I have video.  I can move around to the different desktops but then I'm blind again when I release.  I'm hoping this behavior gives a clue as to what is happening.

I have had my screen saver on random, which leads me to suspect that one of the screen savers is causing the problem, hence the reason it only happens every couple months.  I've switched it to straight blank now and will see if I have this problem in the future.

Here's some information about my system:

kobryan@kob:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
kobryan@kob:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
kobryan@kob:~$ dpkg -l | grep -i radeon
ii  libdrm-radeon1                             2.4.18-1ubuntu3                                      Userspace interface to radeon-specific kernel DRM services -- ru
ii  radeontool                                 1.6.1-0ubuntu1                                       utility to control ATI Radeon backlight functions on laptops
ii  xserver-xorg-video-radeon                  1:6.13.0-1ubuntu5                                    X.Org X server -- AMD/ATI Radeon display driver
kobryan@kob:~$ dpkg -l | grep glx
ii  libgl1-mesa-glx                            7.7.1-1ubuntu3                                       A free implementation of the OpenGL API -- GLX runtime
ii  libglitz-glx1                              0.5.6-1build1                                        Glitz OpenGL library GLX backend
ii  rss-glx                                    0.9.0-2ubuntu4                                       Really Slick Screensavers GLX Port
kobryan@kob:~$ dpkg -l | grep fglrx
ii  fglrx                                      2:8.723.1-0ubuntu5                                   Video driver for the ATI graphics accelerators
ii  fglrx-amdcccle                             2:8.723.1-0ubuntu5                                   Catalyst Control Center for the ATI graphics accelerators
ii  fglrx-modaliases                           2:8.723.1-0ubuntu5                                   Identifiers supported by the ATI graphics driver
ii  xorg-driver-fglrx                          2:8.723.1-0ubuntu5                                   Transitional package for xorg-driver-fglrx
kobryan@kob:~$ grep -v "^#" /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Would any more information be helpful?  If you have any ideas or suggestions, please point me in the right direction.  It is quite irritating when this happens because I have to switch to each desktop and blindly close all my running applications and then reboot.  I've tried switching to a different virtual terminal and restarting gdm but that just froze everything the last time I did it.

Thanks in advance for any advice.

Regards,

Kevin

---

### Post by kobkob on 2010-12-30
No one has any ideas?

---

