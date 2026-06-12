---
title: "Resolution Stuck at 800x600"
date: 2008-05-11
forum: Multimedia Software
---

### Post by orangeLemon on 2008-05-11
Recently I installed Ubuntu Hardy Heron on my computer, only to notice that the resolution was stuck at 800 x 600. I installed my nvidia driver and was able to change my resolution to 1024 x 768, my ideal resolution. Then after some time I uninstalled Ubuntu to do a full partition of Windows, eventually getting tired of it and doing a partial install of Ubuntu with Wubi. The same resolution problem persisted, but whenever I installed my driver the maximum resolution was 640 x 480. I thought this was just a Wubi problem, but after adding Ubuntu as it's own partition the I noticed the same problem persisted. Note that I recently installed Ubuntu HH full just a week ago (Friday the 2nd) and there was no resolution problem (aside from the 800 x 600 problem I described above.) Note that I have tried installing all the updates, and not installing any updates on HH, so I assume the updates are not the problem. 

So I want to know is there any work around to change the resolution, and why something like this would happen when my computer was working perfectly just a week ago.

Nvidia Geforce 4 Mx Integarted (Nvidia-Glx)
512 MB Ram

If any additional information is needed please tell me and I'll respond as quickly as possible. Thanks in advance.

---

### Post by chewearn on 2008-05-12
Have you try to configure the resolution via nvidia-settings?

In Hardy, you need to install it first:
[apt://nvidia-settings](apt://nvidia-settings)

Then, run it with sudo (else you can't save the generated xorg.conf):
```
sudo nvidia-settings
```Make sure to press the button "Save to X configuration File", else your changes might not stick after a reboot.

---

### Post by orangeLemon on 2008-05-12
I tried that but the only resolutions available are 640 x 480, and 320 x 240 with my graphics card enabled. I did notice when using that problem that the configured monitor is CRT-0, whereas my monitor is an LCD screen, could that have anything to do with it? I'd change it but the only available model name is CRT-0. 

[http://img375.imageshack.us/img375/1295/screensb1.jpg](http://img375.imageshack.us/img375/1295/screensb1.jpg)
^Screen of nvidia-settings. 

Also my xorg.conf for my monitor and screen section.

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection
```

---

### Post by chewearn on 2008-05-12
Make sure nvidia restricted driver is installed and in effect.  To confirm, this command should return "direct rendering: Yes".
```
glxinfo | grep rendering
```

Then, back-up your xorg.conf, in case you need to recover (when everything else failed):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You should now run this to auto-generate an xorg.conf with more parameters for the nvidia driver:
```
sudo nvidia-xconfig
```

Following this, reboot your computer.  If you are lucky, you should get back into the desktop with the best resolution.

However, there is a chance that you could be unlucky and drop into low resolution mode.  If this happened, recheck the first command above to see if you are still using the nvidia driver.  If it returns "direct rendering: No", then reboot into safe mode.

Another scenario is you get blank screen upon reboot.  In this case, also reboot into safe mode.

In all cases (whether blank screen, low resolution with nvidia driver, or low resolution without nvidia driver), reboot into safe mode and edit the xorg.conf.

```
nano /etc/X11/xorg/conf
```

Look for these lines under Section "Monitor", e.g.
```

    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 70.0

```

The numbers need to be changed to your monitor specifications.  Find your monitor user's manual for these figures.

Or use the number above as a starting point.  Don't "overdo" it and put in numbers that are too large.  Some trial and error are required, i.e. make a change, save the file, and reboot.  Repeat if still not working.

If after some trials, you are still stuck, restore the original xorg.conf:
```
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by orangeLemon on 2008-05-12
glxinfo | grep rendering
        = 
direct rendering: Yes

sudo nvidia-xconfig
        =
Changed the xorg file to 
```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```
But as far as I can tell has made no difference, as I cannot change my resolution, and as you can see the "monitor" section is fairly blank.  Did the direct rendering thing in the terminal and it still replied as yes. Any more suggestions as to what is causing this is appreciated

---

### Post by chewearn on 2008-05-12
Please add the monitor parameters as outline by my previous post.

---

### Post by thettrix on 2010-01-02
I had the exact same problem as the OP, my monitor was stuck at 640x480 max but everything else was great, direct rendering and all, I was stumped, I did what the guy says running xconfig and rebooting didn't work, but when he posted the refresh rates I looked in my xorg.conf and it didn't have any in there, I pasted what he had in (code) under Section "Monitor" like he says, saved rebooted and BOOM 1024x768! but that's not good enough, so I sudo nvidia-settings and looked at what resolutions were available, it had like every resolution there could possibly be available, so I hit 1280x1024 and now everything is good.

Thanks!!

---

