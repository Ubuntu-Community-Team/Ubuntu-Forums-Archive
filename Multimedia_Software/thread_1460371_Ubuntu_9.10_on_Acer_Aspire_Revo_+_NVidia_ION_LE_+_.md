---
title: "Ubuntu 9.10 on Acer Aspire Revo + NVidia ION LE + XBMC on Vizio L32HDTV walkthrough"
date: 2010-04-22
forum: Multimedia Software
---

### Post by smpn on 2010-04-22
Just wanted to share my experiences over the last few days... I've tried many, many things to get this working and finally figured it out, so hopefully I can save some people the same headaches.  

Initially when I connected to the L32 HDTV over the HDMI cable, picture came up, and I thought great, plug & play.  But the title bar and taskbar were missing and I soon learned that this cheap Vizio TV has a native resolution of 1366x768 and simply upscales and chops off what it considers "overscan" when you drive it at the proper 720p 1280x720.  To add to the problems, it doesn't report the correct EDID modes (look at your /var/log/Xorg.0.log to see the probes or install and use the read-edid package) so 1366x768 isn't an option out of the box.

I spent days mucking around with /etc/X11/xorg.conf with custom Modelines, strange options and  copying confs from other threads, trying to get it working at 1366x768 or 1360x768 or 1368x768 (some variations seem to work for some people)

In the end, I didn't have to touch xorg.conf at all =)  All I had to do was install the newer NVIDIA 195 drivers!!!  Then you get the lovely Overscan Compensation slider in nvidia-settings, and all is well.

First, you will have to apt-get remove the old drivers (probably -185 or -180).  Install apt-show-versions for an easy way to do that.  I had a bunch of junk, I just removed all packages that had nvidia-someversionnumber in the package name.

```

# apt-show-versions | grep nvidia
nvidia-173-modaliases
nvidia-185-libvdpau
nvidia-185-modaliases
nvidia-185-kernel-source
nvidia-96-modaliases

```

Then add the Nvidia PPA and install the new drivers:

```

sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update && sudo apt-get install nvidia-195-modaliases nvidia-glx-195

(later I got messages about ffmpeg, mplayer etc package upgradess being 
held back, which I fixed by doing:)
sudo aptitude dist-upgrade

```

Then reboot (or maybe just sudo restart gdm) and you should have OVERSCAN COMPENSATION slider in the nvidia-settings app (Administration -> NVIDIA X Server Settings -> GPU0 -> DFP0).  Move it around and voila, your top and bottom bars are back!  Hooray!!!

Now the next problem is it doesn't reload those overscan settings when you reboot (boo).

First, from NVIDIA X Server Settings (nvidia-settings) app, make your Overscan Compensation changes, then click on "nvidia-settings Configuration" at the bottom and then "Save Current Configuration".  This will write out the config to ~/.nvidia-settings-rc

Next, from Preferences -> Startup Applications, add a new startup item with the command:

```
nvidia-settings --load-config-only
```

That should do the trick.

PS: My xorg.conf is very very simple:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

Hope that's useful for someone.

- Skye

---

### Post by 'Bokenite on 2010-04-26
Thank you!  Your post saved my remote from being smashed into a thousand pieces!

---

### Post by killsforpie on 2010-07-24
You just saved me a lot of time. Thanks!

---

### Post by andersja on 2010-07-29
Thanks for sharing! 

I have a quick question - if you've tested skype on your machine; are you able to get "HD" or HD calls (640x480 or 720p)? 

I currently have an ageing Celeron laptop as "livingroom skype box" but have been considering getting the Acer Aspire Revo if it can do decent video conferencing. [See also this thread]("http://ubuntuforums.org/showthread.php?t=1541454").

---

### Post by slickvguy on 2011-04-02
Decided to install Maverick on my revo 3610, since win7 is such a pita (bloated/slow/etc). Having the usual overscan / nvidia problems. In the past, I have fixed similar problems using modelines in xorg.conf (which it appears that we aren't using anymore), then using xrandr (which is giving me errors when I try to add modelines. I\ve read xranr is not compatible w/ thi driver version?).

My Revo is connected to an old Hitachi 52" RPTV 1080i native (does 720p too). It\s working fine in 720p mode using win7 and 1132x662/60hz. 

One problem is that the overscan control in the nvidia panel seems to have a mind of it's own. Sometimes it's there - usually it isn't. I have to go through all sorts of different resolutions and keep playing with the control panel, and eventually that slider shows up. lol. Once the slider appears, the overscan slider works just fine. But...

Main problem is that even when I save the settings (as described in this thread), they do not load at startup - nor do they load when I manually run the nvidia control panel or run it from the command line. I checked the file - the settings are definitely correct and in there (for overscan, etc). But it's as if they are being ignored, locked-out, or overridden by something else.

I'm using 260.19.06, which I believe is the current driver (but not the latest on nvidia's website). Is nouveau messing things up? Would appreciate any help. 

p.s. My most recent lcd tv purchase was a toshiba with a "no overscan" mode. What a pleasure. Perfect 1080p w/o hassle.

---

### Post by slickvguy on 2011-04-03
Solved this problem, for anyone who might stumble on this post.
The problem in this specific situation was that something early in the boot process was putting the tv into 1080i mode, and once it was in that mode, it could/would not apply the nvidia-settings. Has to be in 720p to apply the overscan adjustment, etc. So I stuck a xrandr line in /etc/gdm/Init/Default (even though it acts differently on this setup versus my others) to change the resolution to 1280x720, and then the nvidia-settings get applied. Thus the TV goes from being turned on @ 720p, to Ubuntu boot changing it to 1080i, to xrandr changing it back again to 720p, and finally nvidia-setting -l applying ~/.nvidia-settings-rc. lol. Ain't pretty - but it works.

---

### Post by flynx on 2011-10-15
I ran up against the same problem.  Acer Revo with Onieric (still can't spell that) connected to a Sony 52" 1920/1080 TV.  The nvidia overscan slider works at 720 but not at 1080.  It would appear someone doesn't want us watching BluRay movies on our PCs at full resolution.  

Even tried adding the OverscanCompensation line to the /~.nvidia-settings-rc file but the nvidia driver just ignores the overscan setting if it is driving at 1080.  This seems more like a DRM "feature" to me than anything else.

---

