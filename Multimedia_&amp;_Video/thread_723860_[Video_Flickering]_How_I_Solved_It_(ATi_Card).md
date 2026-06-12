---
title: "[Video Flickering] How I Solved It (ATi Card)"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Job_314 on 2008-03-13
So, up until recently I had everything working with my ATi card except some seriously annoying video flickering. Some of you may be using VLC player to force X11 playback. 

Awhile back, I updated Ubuntu, let all the updates download & install. But when it was done, I noticed a huge decrease in performance, videos lag, firefox lags when switching tabs and scrolling, etc. 
          
So, I re-installed Gutsy, used Envy to install my drivers, installed CCSM, and updated to the latest Compiz (using the update manager)... that's all. After fixing the Compiz "**378:** /usr/local/bin/compiz: not found" bug, everything worked... except video. It STILL flickered. So, here's how I got it fixed, it's way easier than I thought.

**Step 1;**
Open your terminal/console... and enter this command; *sudo gedit /etc/X11/xorg.conf*

**Step 2;**
With your Xorg.conf file now open in the text editor, scroll down until you see the "Device" section. It should look something like this...

```
[I]Section "Device"
        Identifier	"ATI Technologies Inc ATI Default Card"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
        Driver		"fglrx"
	Screen	0
EndSection[/I]
```

Now... beneathe the "Driver" line, add this code;

*	Option 		"TexturedVideo" "off"*

So it should look like this;

```
[I]Section "Device"
        Identifier	"ATI Technologies Inc ATI Default Card"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Option 		"TexturedVideo" "off"
	Screen	0
EndSection[/I]
```
[B]
Step 3;[/B]
Click save (make sure it saved). Now, reboot your machine, and whala! No more flickering! :D

I hope this helps someone! If you have questions just ask!
-Austin

---

### Post by Wulfrunner on 2008-03-15
Thanks, this worked with a Diamond Radeon 2400 HD Pro.

---

### Post by petronell on 2008-03-16
Thanks fixed it on my ATI Radeon 2400 card as well.

dr :popcorn:

---

### Post by dootzky on 2008-03-27
My Ati Radeon Mobility HD 2400 (on MSI Megabook EX610X) is not working well at all.
I've got the high resolution, but no direct rendering, and no 3D! :(

on fglrxinfo i can see that i'm still running MESA, instead of ATI.. :( 
any thoughts on how to fix this?

---

### Post by dootzky on 2008-03-28
SUCCESS!! All fix! :)
Here's the link for my solution on this forum:

[http://ubuntuforums.org/showthread.php?t=738592](http://ubuntuforums.org/showthread.php?t=738592)

Hope it helps someone! :)
Cheers,
dootzky

---

### Post by Melcar on 2008-03-28
on AVIVO cards (pretty much anything R5XX and newer) TexturedVideo provides better video playback than the older VideoOverlay (and better overall 2D image quality), so turning it off may cause some issues (especially if you have a really slow card with poor overlay capabilities).

---

### Post by SGAZ on 2008-03-28
Excellent!  Super Improvement!  Thanks for the post!

---

### Post by Melcar on 2008-03-30
Just so you guys know, fglrx (I think starting with 8.1) uses TexturedVideo by default on all AVIVO chips (R5XX and newer) since these chips lack any real 2D engine (TexturedVideo uses shaders to render 2D) and in some VideoOverlay does not even work (either the chip does not support it or the driver does not let you use it), so turning it off on these chips will disable Xv completely.  Your players are most likely reverting to using X to render, hence the no flickering.  On non-AVIVO chips VideoOverlay is used by default, so setting TexturedVideo to off will do nothing; note that on these older chips it is still possible to enable TexturedVideo, which some claim gives them better performance and image quality than VideoOverlay.

---

### Post by themoebius on 2008-04-08
This solved the flickering problem for me, but I seem to get pretty poor video performance unless I run it at exactly 100%. more or less and it get pixelated and a lower frame rate.

---

### Post by pather on 2008-04-11
I'm going crazy because of ATI poor video performance. I've got my pc primary as videoplayer attached to widescreen LCD TV. 
Everything works just fine, except for one thing. And that it is 100% cpu load while watching video with subtitles. 
I'm using Xine as my primary player and i like it, but this issue is driving me crazy :)
Obviously are the subtitles rendered into video by cpu (although I thought it is handled by videocard). If I turn off the option "Use unscaled OSD" cpu load is no more 100% but something like 30% (AMD Athlon 64FX @ 2GHz). But! The subtitles is realy ugly, like scaled image, pixelated like hell... If the "Use unscaled OSD" option is on, subtitles are nice and sharp, but cpu load climb back to 100%.

Now I've tried following this thread and adding the line 

```

Option 		"TexturedVideo" "off"

```

to my xorg.conf makes the same thing like turning off the unscaled OSD. So cpu load is OK, but result is not pretty.

I am using Kubuntu 7.10 and ATI drivers 8.3

here is my xorg.conf part

```

Section "Device"
  identifier "ATI Graphics Adapter 0"
  boardname "ati"
  busid "PCI:4:0:0"
  driver "fglrx"
#  Option "FSAAEnable" "off"
  Option "Capabilities" "0×00000000"
  Option "VideoOverlay" "on"
  Option "OpenGLOverlay" "off"
#  Option "FSAAScale" "0"
  Option "XAANoOffscreenPixmaps" "true"
  Option "AllowGLXWithComposite" "true"
  Option "DisableGLXRootClipping" "true"
#  Option "TexturedVideo" "off"
  Option "TexturedVideoSync" "on"
screen 0
EndSection

Section "Device"
  identifier "ATI Graphics Adapter 1"
  boardname "ati"
  busid "PCI:4:0:0"
  driver "fglrx"
#  Option "FSAAEnable" "off"
  Option "Capabilities" "0×00000000"
  Option "VideoOverlay" "on"
  Option "OpenGLOverlay" "off"
#  Option "FSAAScale" "0"
  Option "XAANoOffscreenPixmaps" "true"
  Option "AllowGLXWithComposite" "true"
  Option "DisableGLXRootClipping" "true"
#  Option "TexturedVideo" "off"
  Option "TexturedVideoSync" "on"
screen 1
EndSection

Section "Screen"
  Identifier "aticonfig Screen 1"
  Device "ATI Graphics Adapter 1"
  Monitor "aticonfig Monitor 1"
  DefaultDepth 24
  SubSection "Display"
    Viewport 0 0
    Depth 16
    Modes "1280x1024@75"
  EndSubSection
  Option  "XvmcUsesTextures" "True"
EndSection

Section "Screen"
  Identifier "aticonfig Screen 0"
  Device "ATI Graphics Adapter 0"
  Monitor "aticonfig Monitor 0"
  DefaultDepth 24
  SubSection "Display"
    Viewport 0 0
    Depth 16
    Modes "1360x768@60"  
  EndSubSection
  Option "XvmcUsesTextures" "True" 
EndSection

```

Here is the option commented, but I've tried with it a few mninutes ago, this is just another test :)
So anyone has some idea? I must admitt, I don't....

It's not crucial thing, but it would be nice if it works perfectly :)

---

### Post by jameskeagie on 2008-04-14
I found a fix that included this command and a few others.  Here's the link to the step by step instructions of what worked for me.  

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by pather on 2008-04-19
This works fine for the fullscreen video, but subtitles are again blurry, like I reported before... 
i think i throw the fu**in ATI from the window and buy nvidia... 

thank you anyway

---

