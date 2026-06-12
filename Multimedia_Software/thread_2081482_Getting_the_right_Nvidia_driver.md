---
title: "Getting the right Nvidia driver"
date: 2012-11-07
forum: Multimedia Software
---

### Post by defaria on 2012-11-07
How do you get the right - meaning latest and greatest - Nvidia driver for an Nvidia G96 [GeForce 9500 GT] (rev a1) on Ubuntu 12.04 LTS 64 bit? Nvidia Settings reports that I have 304.60 but when I go to Additional Drivers I see several lines listed, none really saying what version that they are (see attached) and often when I try to activate them they fail miserably, sometimes causing me to have no Nvidia driver and no X. And I've had many problems with Compiz and Flash so I'd like to make sure my video driver is the correct one. Also how would I remove entries from the attached dialog box that I don't need or that don't work?

---

### Post by drmrgd on 2012-11-07
I believe the drivers that show up as available are just like other packages and only show up if they're in the Ubuntu repositories.  Also, just like other packages, the latest version may have not yet made it to the repos.  So, if you want the very latest, you can head over to Nvidia's website and download the latest from there.  There's a page where you just put the details of your GPU in, and it'll give you the correct driver.  Note, though, that this may have not been fully tested by Ubuntu and may cause problems.  There are also instructions for how to properly install the driver, in addition to, how to disable the Nouveau driver.

Yesterday when I was playing around, I did notice that the latest drivers (R310) are available in the repos, but listed as experimental:

```
sudo apt-get install nvidia-
nvidia-173                        nvidia-cg-toolkit                 nvidia-experimental-310
nvidia-173-dev                    nvidia-common                     nvidia-experimental-310-dev
nvidia-173-updates                nvidia-current                    nvidia-settings
nvidia-173-updates-dev            nvidia-current-dev                nvidia-settings-experimental-304
nvidia-96                         nvidia-current-updates            nvidia-settings-experimental-310
nvidia-96-dev                     nvidia-current-updates-dev        nvidia-settings-updates
nvidia-96-updates                 nvidia-experimental-304           
nvidia-96-updates-dev             nvidia-experimental-304-dev
```

I had considered trying one of those out instead of manually installing the latest.  However, I couldn't take my system down to do the install and haven't tried it.  You might try that as well.

---

### Post by defaria on 2012-11-07
The problem with this is I have absolutely no idea what each one is, what card it even is for nor it's version. That information is simply not there. What's worse is that none of them activate or activate properly. I either get an error or it seems to work and requires a reboot and I do and I get no X running at all because it says the driver is not installed.

I've downloaded drivers directly from Nvidia. I have 310.14, 304.43 and 304.51 in .run files. I .run 'em too. But they error out. I've also seen people say that you can get into trouble installing them as opposed to the Ubuntu tested ones and that the two package systems are not the same and you shouldn't intermix them.

I still have problems with Compiz and Flash and occasionally everything will freeze and then a blink will happen, things will freeze again and then a blink. After several times it usually frees up and gets better. I've seen message about X getting messages like "nvLock: client timed out, taking the lock". Other times I find X taking 100% of the CPU and I have to kill it. That's why I want to make sure I have the correct Nvidia driver running.

Just now an update for the Nvidia driver came in through update-manager. Didn't say what version it was. It supposedly installed it. I don't see anything saying I need to reboot.

But back to the Additional Drivers dialog, the first two lines say "NVIDIA binary Xorg driver, kernel module and VDPAU library" - IOW the exact same label! The next line says nvidia_current and is active. The line after that say again the exact same label. The final two lines say "Experimental NVIDIA binary xorg driver, kernel module and VDPAU library", again the same label. As such how are you supposed to tell them apart?!? 

Looking at the lower part of the dialog, when I select the first line I see:

 ```
The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported.

 This package also includes the source for building the kernel module required by the Xorg driver.

 GPUs ranging from GeForce series 5 to GeForce series 9 are supported.

 See /usr/share/doc/nvidia-173-updates/README.txt.gz for a complete list of supported GPUs and PCIIDs
```

Selecting the second line I see the exact same thing. I can only make two assumptions here. First they must be the same thing (so why list it twice?). Second I'm guessing this is for the 173 version.

Moving to the 4th line I see:

```
The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported.

 This package also includes the source for building the kernel module required by the Xorg driver, and provides NVIDIA's implementation of the Video Decode and presentation API. The latter enables acceleration for GeForce 8 and later series cards for h264 video.

 GPUs such as GeForce series 6 or newer are supported.

 See /usr/share/doc/nvidia-current-updates/README.txt.gz for a complete list of supported GPUs and PCIIDs
```

I have no idea what this is for except to say it says "nvidia-current-update". Must be current but there is no indication of what version this is at all! It talks about GeForce 8 and later series cards but my card is a 9500. I'm not sure if 8 refers to say an 8000 series and 9500 would be considered a "later series" or a totally different series.

For the two experimental lines they say:

```
3D-accelerated proprietary graphics driver for NVIDIA cards. May be required for some newly released 3D software and games.

 WARNING: This is an unstable beta driver.  This package is intended for testers and early adopters, and not recommended for production hardware.

 Release Notes: https://plus.google.com/u/0/118125769023950376556/posts/bHW91CsG4bP

 See /usr/share/doc/nvidia-experimental-304/README.txt.gz for a complete list of supported GPUs and PCIIDs
```

With the only difference really being 304 vs 310.

Going for the last one, the 310 experimental, I say activate and it says it's installed it and I need to reboot. I will reboot and come back around to describe what happened...

Interesting... I rebooted and apparently I'm using 310.14! Many things still fail however. For example:

. I use Compiz - not Unity. When I boot up on my desktop Compiz is no where to be seen - no window manager at all! I have to start Compiz.
. Windows started before Compiz have an annoying habit of jumping to the top of the screen after I start Compiz and when focus goes from one of those windows to another.
. Workspaces don't work. Dragging a window from one workspace to another results in the mouse being like 1000 pixels from the window being dragged.
. My screenlets don't start.
. Skype, which I run at start up, is nowhere to be found in gnome-panel. I have to kill it and restart it.

---

### Post by drmrgd on 2012-11-07
Hmmm....well, I no where near a driver expert by any stretch (I just usually get lucky when I try to install them I guess).  I've always found Jockey to be a hot mess when it comes to deciphering what is actually installed and running, and what is available.  So, I'm with you there!

Not sure if you saw it or not, but this post was just put up today, and looks to be a great guide on updating your Nvidia drivers:

[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

You might have a look to see what you may or may not be missing from there.  Hopefully someone with a little more knowledge may come by to help.  It sounds like you're installing the drivers OK, but still having some kind of residual problems that I've never faced (thankfully!) myself.

---

### Post by defaria on 2012-11-08
I agree with your assessment. Indeed Compiz starts OK on my laptop but not my desktop. 

Interestingly, one of the descriptions on the experimental package said "Release Notes: https://plus.google.com/u/0/118125769023950376556/posts/bHW91CsG4bP". I thought to myself, hmmm... A google+ link? Odd. Turns out it's a link to some dudes Google+ profile - apparently one of the driver engineers. I emailed him and invited him to participate in this thread. We'll see if he does. I'll post any summary information that I find out.

I'm just glad to be on a relatively later version of the driver now. Some things like Flash **seem** a bit more stable. Still like to work out the Compiz stuff though...

---

