---
title: "Graphical Corruption and Freeze on ATI"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MikeMLP on 2010-09-25
Hi all,

I'm hoping you can help me find the right package to file a bug report on.  

I am experiencing an issue where horizontal "stripes" appear on the right side of the screen, each about 1/2 an inch in height and about 1 inch in length.  Each "stripe" appears as a gradient going from transparent to black from the top of the stripe to the bottom.  Notification bubbles are pushed  off the right side of the screen, so that only the left half of the notification bubble appears.  The Me menu, and other right-aligned menus are similarly "pushed off" the right side of the screen.

I would post a screenshot, but usually the computer hard-locks within a a few seconds of the appearance of the desktop.  The issue first presents itself at the login screen.  The problem appears whether Compiz is enabled or disabled, but clears up if I boot into failsafe X.

I have an IBM T42 with a Radeon Mobility 9600.  I've been upgrading since alpha three, but I just tried a daily livecd image, and the problem appears there too.

The problem first appeared after an update on Sept. 14 or Sept. 15.

A few of the packages that were updated during that time (and seem to me to be the most likely culprits) were:

xserver-xorg-core
xserver-common
libglu1-mesa
libgl1-mesa-dri
libgl1-mesa-glx

All of the above packages were later updated after Sept. 14 or Sept. 15, but the problem remains.

Can you help me out?

Edit: I should also mention that I use the free ATI driver, not fglrx

---

### Post by MikeMLP on 2010-09-25
So, this problem isn't quite as bad as I first thought.  I was able to get to the desktop without a freeze, where I discovered that the screen resolution had been set to 1600x1050, not 1400x1050, which is the proper resolution for this screen.  So it seems it is an autoconfiguration problem.  

Anyone happen to know the right package for auto-configuration of screen resolution?

---

### Post by koma77 on 2010-09-26
I'm experiencing something very similar.

I also have a laptop with Radeon Mobility 9600 running the free driver.
Since I upgraded to Maverick beta I have not been able to login to gnome for more than a few seconds, then a hard freeze occurs.

However, for me the screen was "rotated" about 1/5th of a screen sideways so that the very rightmost 1/5th of the screen is on the very left instead.

I added a kernel parameter (radeon.modeset=0) that solved the "rotated" problem, but the hard freeze still occurs.

The problem is, I don't know how to check for screen resolution without using gnome.

I have a minimal xorg.conf with no screen resolution in it...

---

### Post by ktp on 2010-09-26
> **MikeMLP said:**
> So, this problem isn't quite as bad as I first thought.  I was able to get to the desktop without a freeze, where I discovered that the screen resolution had been set to 1600x1050, not 1400x1050, which is the proper resolution for this screen.  So it seems it is an autoconfiguration problem.  

Anyone happen to know the right package for auto-configuration of screen resolution?

You can use **xrandr** command to see the resolutions that are detected.

---

### Post by koma77 on 2010-09-26
I tried to boot from a LiveCD of the official beta release, and there was no freeze then!

It also uses the radeon driver but with no xorg.conf at all. Resolution is the same as mine, so at least for me that was not the problem.

Clearly something is different: if I boot with the radeon driver and no xorg.conf I don't get this good graphics...

---

### Post by MikeMLP on 2010-09-26
I have a feeling that the freeze I was experiencing has something to do with the relative slowness of this old laptop's hardware, compared to modern hardware - it seemed to happen when doing a lot of cpu/gpu intensive things at once (e.g. loading multiple tabs simultaneously).  The freezes have become less frequent with successive updates, but still happen from time to time.  

This is the output of xrandr:

```
~$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      50.0*+
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9     56.2  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

Monitor Preferences (System->preferences->monitor) lists the same resolutions.  

I'm guessing that the magic auto-config program sets the screen resolution to the maximum supported.  The max supported resolution is being detected at 1600x1024, even though the panel can support no greater a resolution than 1400x1050, causing the problem.

I was able to "sort of" fix the problem by setting my screen resolution to 1400x1050 in Monitor Preferences.  However, the login screen still displays at 1600x1024.  I "fixed" that by enabling auto-login.  

Clearly this is a bug.  Should I file a bug report against xrandr, then?  Or a different package?

---

### Post by ktp on 2010-09-26
I would file it against the driver (xserver-xorg-driver-ati) since xrandr shows correct resolutions.

Also I wonder if you have /etc/X11/xorg.conf.  If you do can you try without it.

---

### Post by MikeMLP on 2010-09-26
Nope, no custom xorg.conf for me - I like having little configuration to do.  xrandr does seem to be working properly - I checked the output on an 10.04 livecd, and the output is the same as it is on 10.10.  It is whatever package that decides what the "optimal" screen resolution is that is making an error.  Probably, as you say, the free ati driver.

---

### Post by koma77 on 2010-09-28
Just an update on the (at least very similar) problem:

I tried a 10.10 Beta Live CD and it worked fine. The radeon module was loaded, desktop effects were on, and there was no freeze.

So, I took the drastic step of reinstalling ubuntu completely to 10.10 beta.

But now I get the problem on my new installation. It works just as bad as before...

Strange.

---

### Post by rapiertg on 2010-09-28
I do have the same issue. Seems that xrandr cannot read EDID (a chip in monitor that stores the data about your monitor). I am currently looking for a method of disabling xrandr or corrupted resolution.

My topic is in here, but couldnt found help:
[http://ubuntuforums.org/showthread.php?t=1581622](http://ubuntuforums.org/showthread.php?t=1581622)

---

### Post by Souris on 2010-09-28
Same problem here

with a 21" HANNS-G Hi221 max res 1680x1050 and ATI Radeon HD 4200

Ubuntu goes 1600x1200 => out of range

I had to change my resolution manually (reboot with failsafe X) and use autologin

same problem with open source drivers and fglrx ...


Souris

---

### Post by Souris on 2010-09-28
MikeMLP, ktp

clearly xrandr does NOT shows correct resolutions : 1600x1024 is incorrect for MikeMLP configuration !!!

so I suppose a bug report against xrandr is a good choice


Souris

---

### Post by Souris on 2010-09-28
My settings :

~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
CRT1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   1680x1050      60.6*+   60.0  
   1600x1200      75.0     60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1366x768       59.9  
   1360x768       60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   640x480        75.0     72.8     60.0  

[IMG]http://dleger.free.fr/Capture.png[/IMG]

Souris

---

### Post by Jim March on 2010-09-28
I saw something like that briefly after letting my system run a relatively long time (well over a week of hard use) with no reboots, just sleep (when *I* slept too :)).  I use open-source Radeon drivers on an X1700 card (actually FireGL V5250 but the drivers consider them the same - Thinkpad T60P lappy).

When I say "briefly", my screen went to horizontal lines for a bit, glitched a bit more but then sorted itself out.  It did NOT mis-report the video resolution (1680x1050) and when it came back, it was OK.  I rebooted normally shortly thereafter, haven't seen it again.  I thought it was locked up for a moment, but it played Pandora audio the whole time cleanly so clearly the CPU/kernel wasn't out to lunch, so I waited a bit and it was back.  Whole thing was maybe 30sec. long.

I suspect something in the open-source drivers, and whatever it is affected me less than the even older 9600 card.

---

### Post by MikeMLP on 2010-09-28
I haven't posted a bug report yet because I'm still not sure which package is the correct one.  I know that I said, > Probably, as you say, the free ati driver but, I just remembered that the free ati driver wasn't one of the updates I received when the issue first arose.  Neither was xrandr.  xserver-xorg-video-intel was upgraded around that time, but I don't use it.

> MikeMLP, ktp

clearly xrandr does NOT shows correct resolutions : 1600x1024 is incorrect for MikeMLP configuration !!!

so I suppose a bug report against xrandr is a good choice


Souris

I do realize that 1600x1024 is out of range.  The strange thing is, I ran ```
xrandr
``` from a lucid livecd, and the output was the same as it is in Maverick.  Maybe my issue is the result of two bugs working in concert.  A latent xrandr bug, plus a new autoconfiguration bug.  

@Souris:  Was your out of range issue something that appeared on its own through an autoconfiguration gone bad, or did you manually set your resolution to an out of range resolution (that, if I understand correctly, xrandr shouldn't have offered as an option in the first place)?

---

### Post by Souris on 2010-09-29
MikeMLP:

Yes, my out of range issue appeared on its own

... and I already have 3 computers affected,

I'm waiting for this bug to be resolved, before I can migrate more computers to Maverick

I have many computers with this config : HP Compaq 6005 + HANNS-G Hi221

I work in a city council in France near Paris

I know it's beta, but 10/10/10 is near...

Crossing fingers...


Souris

---

### Post by Souris on 2010-09-29
Now posting my xrandr under lucid (same computer/screen - live CD) :

LUCID:
~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   1680x1050      60.6*+   74.9  
   1600x1200      75.0     60.0  
   1400x1050      74.9     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  


MAVERICK:
~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
CRT1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
1680x1050 60.6*+ 60.0
1600x1200 75.0 60.0
1400x1050 60.0
1280x1024 75.0 60.0
1440x900 59.9
1280x960 75.0 60.0
1366x768 59.9
1360x768 60.0
1280x800 75.0 60.0
1152x864 75.0 60.0
1280x768 74.9 59.9
1280x720 60.0
1024x768 75.0 70.1 60.0
800x600 72.2 75.0 70.0 60.3 56.2
640x480 75.0 72.8 60.0

Some differencies, but incorrect 1600x1200 was already here under Lucid...

So I don't know what to think about this, and how to report this bug ...

Now looking for already posted bugs on launchpad ..


Souris

---

### Post by rapiertg on 2010-09-29
On ati open source driver everything is ok, but fglrx is causing out of sync here. Made some searching  and it probably should be reported for xorg package:

[https://bugs.launchpad.net/ubuntu/+source/xorg](https://bugs.launchpad.net/ubuntu/+source/xorg)

 or fglrx-installer.

I tried to disable xrandr. But there seems to be 2 packages, one in ati's driver and one in the OS. According to log if i disable one the second one takes its place and sets 1600x1200 :confused:

Found interesting article on debian site here under: IV.1
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by koma77 on 2010-09-30
I'll try to debug my total freeze a bit. Does anyone know if the serial console is enabled by default?

If not, how can I enable it?

And is there any way to enable Magic-SysRq without recompiling the kernel?

---

### Post by danbuter on 2010-09-30
Did anyone actually submit a bug yet? If so, please list it so others can confirm.

---

### Post by rapiertg on 2010-10-01
I haven't, but found one already submitted. If you are affected please mark so:
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/601376](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/601376)

---

