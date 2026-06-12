---
title: "Choppy (unwatchable) mp4 video"
date: 2011-07-01
forum: Multimedia Software
---

### Post by MASEngr on 2011-07-01
Hi everyone.

I am having trouble watching mp4 video on my netbook.  It's a Samsung NF-210, a dual-core 1.5GHz machine with 2G RAM.  It's got 11.04 installed. 

When playing mp4 movies, the sound is in time but the video will only play once every 10-20 seconds.  I've installed various codecs to try to get it to work more smoothly, but realistically if I'm getting any video at all then there's a good chance that the codecs are correct.  The problem persists if the video is on the SD card, the hard drive, or over the camera's USB connection. 

Now, you may suggest that it's the hardware; certainly other solutions have been to "get a better computer".  However, the movies play flawlessly under the Win7 install on the same machine.  Ubuntu requires less RAM (500 MB less) than Win7 so the video should be fine in Ubuntu hardware-wise.  Win7 allows smooth video on the camera or SD card as well as from the HDD. 

Moreover, the camera in question has a component out cord and it will play the movies just fine on my TV.  I am fairly certain that the camera has lesser specifications than my netbook, thus the issue would point to software vs. hardware.

What can I do to get these movies working better on my netbook?  What other information is required to get to a solution?

Thanks,
M

---

### Post by wolfen69 on 2011-07-01
What kind of video card is it? Have you installed video drivers for it?

---

### Post by MASEngr on 2011-07-01
It's an Intel video card, so I shouldn't have to install extra drivers:

"If you have an Intel video chip, you do not need a restricted video driver. Intel's official driver is Free Software (open source) and is bundled with Ubuntu (and most other distributions)
"
From: [https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)


:~$ sudo lspci |more

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

---

### Post by JohnnyC35 on 2011-07-01
What program are you using to play the video? I have a dual 1.6 motherboard and have had issues with some video formats. I have tried using mplayer, and totem, tried tweaking vlc. I have found that xbmc is the way to go. It seems to play any video/audio format regardless if I have good/bad/ugly installed. I am able to run video, hi-def video, 720, and 1080 videos without any stuttering.

You could check Hardware Drivers under Administration, but I don't think you need to install drivers on an Intel video card.

---

### Post by Duncan Williams on 2011-07-01
you will also get choppy, frozen, etc, video playback (mp4, flv, etc) if your window manager, 3d/opengl, compositing settings are not working correctly.

tools:
ccsm   > [http://wiki.compiz.org/CCSM](http://wiki.compiz.org/CCSM)
cfi    > [http://wiki.compiz.org/CompizFusionIcon](http://wiki.compiz.org/CompizFusionIcon)

---

### Post by BicyclerBoy on 2011-07-01
Your machine uses the integrated pineview GPU GMA 3150 with a dual core atom.

The standard ubuntu distro intel driver is possibly not up to date.

My atom netbook uses the old GMA900 & I had to update the intel driver with 10.10
 remix & 11.04 (with unity) if any graphics performance was needed. 
Unity 3d would not work without xorg-edgers ppa.

The ppa to try is xorg-edgers..
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty)

Your netbook has superior graphics (comparatively) & CPU to the old atom 945GME chipset & that can playback H264 576i50 (broadcast rate mpeg2-ts).

---

