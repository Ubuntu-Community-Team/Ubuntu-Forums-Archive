---
title: "ATI X1300 FGLRX Issues"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by payamazadi on 2007-12-26
Hi,

It seems I've been through every guide on the net for installing FGLRX (and even ATI's proprietary drivers) for Radeon X1300 with no luck. I've done about 6 clean installs and still can't get the driver to be enabled - according to:
- fglrxinfo
- Restricted Drivers manager (though at certain times it showed it as enabled just not in use)
- Screens and Graphics control panel

I've tried the unofficial ATI guide at cchtml and couldn't get it to work. I've tried simply enabling the drivers from the restricted drivers manager, and even tried installing ATI's proprietary drivers according to AMD's website. Depending on what exactly I do with the above methods, I either get:
- a black screen where NOTHING works except for num/scroll lock
- an error message telling me that I'm running in low-graphics mode, restricted resolutions at 73hz

Whenever I did a fresh install I always installed the updates (which came out to 149 in all), and still nothing. I've gotten to the black screen about 10 times now, and subsequently have done
```
sudo dpkg-reconfigure  xserver-xorg
``` from booting into recovery mode several times. I've also tried manually editing my xorg.conf file multiple times with the same issues.

I made sure to look through all related threads and of course read the sticky on installing the drivers but the same issues have occurred as listed above.

I am running Gutsy 7.10 on a:
Intel D845Gerg mobo
Visiontek Radeon X1300 512MB AGP8x
512MB PC2700 RAM on an Intel 2.4ghz P4

fglrxinfo returns:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

^- as that error appears in the Unofficial ATI guide, I tried doing the remedies as described there but to no avail.


Thanks in advance to all:guitar:

---

### Post by chuckao on 2007-12-27
I have the same problem with xorg-driver-fglrx (from ubuntu repositories) and mesa. (I have an ATI x1300)

Before last kernel update (2.6.22-14) my fglrx was working perfectly.

I tried Unofficial ATI Guide to install catalyst 7.11 and it works for few days but this version has many bugs (sometimes appears horizontal bars in my cursor mouse   and in the right bottom corner of my monitor).

So, I tried the new version (7.12or 8.443.1) from ATI but again ATI provides many bugs and in this version I can't set 1680x1050 resolution. 

Now I'm trying to use the deb from ubuntu repositories but 'mesa' is not helping me :(

---

### Post by zhouxing on 2007-12-27
Have you guys tried Envy?

[HTML]http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu4_all.deb[/HTML]

---

### Post by chuckao on 2007-12-27
I didn't try envy but it sounds like a front-end for Unofficial ATI Guide. Envy will try to get the last ATI driver and it doesn't work for me because it doesn't allow 1680x1050.

cheers.

---

### Post by payamazadi on 2007-12-27
Tried it tree times on two different drivers with one fresh OS install and I'm still getting a black screen. I even made sure Composite was disabled - the xorg.conf looks completely normal and all the settings look correct but I'm STILL getting a black screen on startup!! When it's enabled and I boot into recovery mode (otherwise I get a black screen), fglrxinfo gives me a no display error, and when I restore default xorg.conf and use the vesa driver fglrxinfo gives me the Mesa bit.

I know if I switch to my Nvidia P162 it'll work, but that's a MONSTROUS step down from an ATI X1300.. especially considering Nvidia stopped supporting it a LONG time ago..

Any ideas? Perhaps there is some issue with the out-of-the-box setup of Ubuntu and the fact that my card is AGP?..

-- From first installation to first use Ubuntu has been nothing but orgasmic for me, but my video card not working is a real deal breaker.. though if I can get it to finally work I'll be ditching Windows completely (and forever).

---

### Post by moron on 2007-12-27
> **chuckao said:**
> I didn't try envy but it sounds like a front-end for Unofficial ATI Guide. Envy will try to get the last ATI driver and it doesn't work for me because it doesn't allow 1680x1050.
cheers.

Before you write off the new driver doing 1680x1050 make sure that you have tried resetting the resolution using the "amdcccle" config / status tool.  Launching this app and then changing the resolution to something lower than 1680x1050 (hit apply) then back to 1680x1050 (hit apply) fixed up the res for me, at least on my X1200 based motherboard.  Looks like a bug in the initial start up settings.

I too though am seeing odd bits of corruption in the mouse cursor.  And still no Xv support.  But at least widescreen is working again.

Cheers

---

### Post by moron on 2007-12-27
> **payamazadi said:**
> Tried it tree times on two different drivers with one fresh OS install and I'm still getting a black screen.

Is the machine actually locked up or if you hit control+shift+backspace do you end up back at a shell prompt (also try control+alt+2)?  It could be a case of bad default settings maybe if X is actually running, like perhaps it is outputting the video to an alternate out or something like that.   What does your monitor's menu say if you go into it - any chance the monitor is blanking out because it is getting a signal at some resolution or frequency it cannot handle?

Cheers

---

### Post by Yellow Pasque on 2007-12-27
Yeah, if you're getting a black screen and/or "no usable screens found" or such, the problem lies in xorg.conf Do you have the correct Bus ID?
Run:
```
sudo update-pciids
lspci | grep VGA
```

Example: Mine says:
```
00:01.0 VGA compatible controller:....
```
so the line in my xorg.conf Device section says:
```
BusID     "PCI:0:1:0"
```

---

### Post by payamazadi on 2007-12-27
argh, finally got SOMETHING -

using Envy i installed the 8.40.4 driver (no matter what i did the 7.12 would yield black screen and and 8.28.8 wouldnt even run - none of the hotkeys you listed worked either), made sure the BusID was correct and disabled composite (according to the Unofficial cchtml guide). rebooted and it started normal.

this is the iffy part - fglrxinfo still yields Mesa strings, but the Screens and Graphics control panel (System > Administration > Screens and Graphics) the graphics tab shows the driver as fglrx, but
all video playback is even choppier and crappier than it was on the vesa driver, which leads me to believe that the driver is working (sigh). and of course i cant enable desktop effects because i cant have composite enabled.

is this what im stuck with? a $150 video card for pixelated ultra-choppy video playback on ubuntu? or is the driver still not working?

any other ideas? this is so discouraging.. 

though now that ive plugged in my 2nd monitor, i get a display on it (mirror of the default screen even though in the screens manager its disabled, and cant enable 'extended desktop' without getting 'out of range' error on my 2nd monitor). perhaps that may be why video is SO choppy - because for some reason the card is outputting the same video to two monitors?.. 

thanks all you guys for the replies!!!!

---

