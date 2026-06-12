---
title: "Xvid video playback in gxine not as good as WMP in XP"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by arjones85 on 2007-10-05
Well, another issue with xvid playback. I have noticed that when the video is moving and/or there are bright flashes, it sometimes looks blocky or sharp-edged on the bright flashes, or during movement line quickly appear and disappear throughout the video, whereas on the same playback under XP with Divx (not Xvid), it looks much, much nicer. Smooth-edged, not blocky, no issues.

Any troubleshooting steps or techniques to use regarding gxine/xvid to increase the playback quality of divx videos?

---

### Post by dfreer on 2007-10-06
Could it be due to your video card, perhaps (are the correct drivers installed)? I haven't noticed any issues with Xvid/Divx movies with my Nvidia 7400.

---

### Post by arjones85 on 2007-10-06
I should be using the correct drivers, I am using the restricted ATI drivers on an ati xpress 200m

---

### Post by chochem on 2007-11-16
I'm believe I'm experiencing the exact same issue with the exact same card. I have installed the proprietary driver for the card. Playback - whether in Totem or VLC - is blocky, especially of course when the placback window is increased in size but even on a 1:1 basis. I'm also running dual-boot and can compare the same version of VLC (0.8.6c) running on Windows and on Ubuntu - and it's not in Ubuntu's favor :(

I've put up a screenshot of a dvd menu (1:1) to give you the general idea.

[http://pics.viharpander.dk/posts/screenshot_ubuntu.png]("http://pics.viharpander.dk/posts/screenshot_ubuntu.png")

---

### Post by disturbed1 on 2007-11-16
For mpeg4 playback (A.K.A. divx, Xvid), while using VLC, right click on the movie windows and adjust post processing. The Xvid decoder playback for windows has post processing enabled by default.

There is 0, none, nada, difference between mpeg2 streams with VLC in Ubuntu and in Windows using properly configured drivers and the **XV** overlay mixer in Linux. If you use XWindow, GL, GL2, and/or have fiddled with your xorg.conf file, your playback of video files can be sub standard. As there should be no difference considering VLC uses the exact same decoder libraries regardless of OS ;) The only differences between video playback on windows Linux, or MacOS is the overlay mixer involved to draw the actual image on screen. XV offers the highest quality overlay while using the lowest resources.

The blocking and fuzziness on mpeg4 videos during playback is a common issue while using XWindow overlay mixer. Also, gxine has several real-time playback filters for noise reduction among other things, that can actually yield a higher quality image than using WMP to playback an Xvid file.

If you're hell bent on using a closed source proprietary codec, with fewer features than Xvid, divx is available for Linux. [http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)

---

### Post by chochem on 2007-11-18
Okay. Thanks for the postprocessing tip but it doesn't change anything. 

As for overlay mixers I'm pretty much in the dark. For a start I don't actually know what they do or where I'd look to check which one I'm using....

As for the divx/xvid codecs - surely that can't be the issue if dvd playback's affected as well? And VLC and Totem do not use the same codecs, right? So if the playback looks equally blocky regardless of player, it I figure it shouldn't be related to codecs...

And maybe I'm approaching this from the wrong end but I figured that it would be an issue that was somehow related to the graphics card / driver since the other guy also has that dratted radeon express thing?

---

### Post by disturbed1 on 2007-11-18
It depends on a few factors.

Your video card and driver used.

Player frontend + backend. Totem can use GStreamer or Xine

Overlay mixer being used.

You have described common video playback issues that involve using the Xwindow (X, X11) overlay system. In VLC, hit settings, choose preferences. Bottom right, click advanced options. On the left pannel, drill down through Video, to OutPut modules, choose XVideo (see screen shot).

This is also a common problem with ATI's FGLRX driver. FGLRX does not support a normal XV overlay, but instead uses GLTextures to display the image. This causes a few problem with video tearing, artifacts, and may conflict with newer versions of Xorg since it has AIGLX enabled by default. Even the newest FGLRX which finally includes the necessary extensions for AIGLX to work, exhibit the same video overlay issues. There really is not a fix for this. If possible use the ATI/Radeon Xorg driver rather than FGLRX.

I personally do not have any playback issues with the system listed in my sig. I also don't use compiz-fusion, and have aiglx explicitly disabled in xorg.conf.

Since you elated to the same problems seen regardless of video type and player used, this leads me to believe it's either an overlay issue, driver settings issue, non optimal (ATI) video card for Linux. ATI does have a couple of xorg.conf settings you can change, such as GLOverlay on/off, and XVOverlay on/off. You may want to try these. Also, mplayer is capable of using the GL and GL2 overlay mixers. These may use more CPU cycles, but might provide the same quality as XV when used with a video card that supports proper overlay calls.

---

### Post by chochem on 2007-11-20
Thanks for the thoroughness of your reply and taking the time, disturbed1 :)

My attempts:
1) Tried disabling restriced drivers and rebooting. Xvid playback in VLC (with default video output module)/Totem reduced to smudged vertical lines. Enabled restriced drivers & rebooted.

2) VLC: Tried switching output module as suggested. No apparent change.

3) VLC: Tried switching output module to OpenGL. Perfect. Well, I tried playback on a .wmv file and it looked great. Then I tried opening a xvid/divx file and playback looked blocky again. Seems like VLC switches back to default on it's own when divx/xvid files are opened??

4) Looked up FGLRX and AIGLX :) Located a [web site]("http://wiki.x.org/wiki/radeon") with said driver but I'd rather wait till all  other options are exhausted.

5) xorg.conf: Basic settings for the X window system, yes? /etc/x11/xorg.conf, yes? I opened it but I'm not entirely sure how to edit it... I found no mention of AIGLX (though there was a section "Module" that loaded "glx"?) nor of the overlay issues. Should I add them myself (and if so, how?) or ought they be there? 

As for AIGLX and compiz-pizzaz: I don't use it and I'd gladly give it up for proper video playback. Seeing how I can't actually change the "Visual Effects" setting from none to something else, I guess it doesn't make that much difference.

Ah! A breakthrough :) I only just figured out that Totem and Mplayer aren't the same thing. I installed mplayer, switched to GL2 and playback is for once not blocky. I'd still like to know about xorg though :)

---

### Post by disturbed1 on 2007-11-20
Since you're using an ATI card, you have a couple of choices. You can use FGLRX which can be installed using the restricted driver manager, or use the open source driver built into Xorg called radeon. To know which driver you are currently using, look at xorg.conf under the driver section. It should say either ATI, Radeon, FGLRX, or VESA. ATI and Radeon are essentially the same thing.

I personally don't use ATI cards anymore. Haven't had any luck. The 200m sounds like a mobility chipset, meaning laptop? If it wasn't for the laptop, I'd suggest picking up a nice $30 nVidia card. My $30 FX5500 outperforms an ati x1600 pro $150 in Linux by night and day.

To edit your xorg.conf file, run this command by pressing alt-F2
**gksu gedit /etc/X11/xorg.conf**
You have to be root to edit system files, which is what the gksu does.

If you're using the ati/radeon driver, take a look here -
[http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html#toc4](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html#toc4)

For fglrx, in a terminal do 
**man aticonfig**
or
**aticonfig --help**

to explain the options.

You should always back up your xorg.conf file, and try to only change one option at a time. I usually do this -
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
this copies your xorg.conf to xorg.conf.backup.
If something goes wrong while trying out different options, you can choose to boot into single user mode at the GRUB menu then just do this to restore the backup
**mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf**
this replaces xorg.conf with xorg.conf.backup

---

### Post by chochem on 2007-11-20
I checked up on the drivers and it seems that the ati/radeon one is present on the system (according to synaptic) so this must be the one that the installation had set up prior to being replaced by fglrx. I did ```
sudo aticonfig --overlay-type=opengl
``` and with vlc set to the same, blockiness is gone from xvid videos too, at the cost however of the 10-15 topmost pixels of the screen (not the playback window) flickering. Disabling overlays:  ```
sudo aticonfig --overlay-type=disable
``` gets rid of the flickering entirely. 

I wasn't paying too much attention to processor strain while switching around but you're probably right about the increased computing power used as simply playing an xvid video consumed upwards of 66%

And sadly, yes, it is a laptop chip. I bought a cheap FujitsuSiemens last year and the weaknesses have shown: The celeron cpu was burning red, hot holes in the table and now my grpahics card turns out to be [evil]("http://en.wikipedia.org/wiki/Image:Richard_Stallman_sign_ATI.jpg") :(

Thanks again for your help, disturbed1. I think I'm gonna leave it at this - if it ain't [more than 50%] broken, don't fix it.

EDIT: Of course, I might have told myself that applications that rely on the overlay system are now f***ed. Running a small 2D windows freeware game under wine and going fullscreen slowed the proceedings to a halt :(

---

### Post by stunner on 2007-11-20
I have an ATI 200M (fglrx, xorg) and all formats play fine using Xv.

You probably want to (1) run aticonfig --overlay-type=Xv and (2) set video preferences in whatever player you use to select Xv.

One thing to note is that Xv tends to support only one video being played at a time; I find that opening multiple videos at once results in the first using Xv (looks flawless) and the rest use X11 (blocky exactly like in your screenshot).

If you use xgl/compiz/fglrx, this is a different matter altogether.  I would suggest searching the forums for the nonXgl script, which is what I use for watching videos when running xgl.

Also, I've had bad experiences with GL/GL2 as a video overlay.  I strongly recommend Xv.


One last thing: run xvinfo to confirm that Xv is enabled and working.

---

