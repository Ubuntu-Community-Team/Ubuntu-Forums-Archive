---
title: "EasyCap Woes"
date: 2011-10-22
forum: Multimedia Software
---

### Post by Rybuger1 on 2011-10-22
I recently purchased an Easycap and tried to install it using[these drivers](http://sourceforge.net/projects/easycapdc60/?_test=beta). My computer runs Xubuntu 11.04.  The sound works perfectly.  However, the video is a mess.

[img]http://www.majhost.com/gallery/rybuger1/Misc/Anythingelse/easycapwoes/easycap3.png[/img]

This is what the Wii Menu looks like through the Easycap.  Not only is the resolution signicantly lower than it was when I did a recording on Windows, it's in black and white.  Even worse, the frame was brutally split three ways!  ([**This**](http://www.majhost.com/gallery/rybuger1/Misc/Anythingelse/easycapwoes/easycapmenufix.png) is my attempt to reassemble the frame.  There's a bit missing.)

I've tried to re-install the drivers several times, but the results have always been the same.  Can anyone help?

Thanks,
Ryan

---

### Post by no2498 on 2011-10-23
install guvcview shut the package manager
now open a terminal type dmesg click enter
look close to the bottom ? did it load a webcam grabber
now type lsusb click enter 
try the cam in guvcview

---

### Post by rmt1947 on 2011-10-23
Yes, at the very least we need to see the output of the command

```
lsusb
```

while the EasyCAP is plugged in.

Mike

---

### Post by Rybuger1 on 2011-10-23
@no2498:  I'm not sure what you mean by a webcam grabber.  dmesg did, however, show the Easycap.  If you'd like, I can show you what it said about it.  Guvcview gave the same quality as previously.

@rmt1947: Lsusb turned up:```
ID 05e1:0408 Syntek Semiconductor Co., Ltd 

```

Thanks,
Ryan

---

### Post by rmt1947 on 2011-10-23
Hi Ryan,

Your EasyCAP with USB ID 05e1:0408 ought to work successfully with the driver from SourceForge on Ubuntu 11.04, although there is a potential complication caused by a clash with the default easycap driver supplied in the staging directory of recent Linux kernels as explained in my post #209 in the main Ubuntu easycap thread:

[http://ubuntuforums.org/showthread.php?t=924504&page=21](http://ubuntuforums.org/showthread.php?t=924504&page=21)

But I'm wondering if your problems are simply something to do with your video source.  I've never used the Wii console myself, but I believe that both PAL and NTSC models are available.  Are you sure you are asking the driver for the appropriate TV standard?  Assuming you are using mplayer to display the video (recommended), for PAL you need a command line like

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:noaudio -hardframedrop
```

whereas for NTSC you need

```
mplayer tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=30:noaudio -hardframedrop
```

If you are not using mplayer for display, what program are you using?

Mike

---

### Post by Rybuger1 on 2011-10-24
@rmt1947:
Previously, I tried to use Cheese to record the video.  The Mplayer script is better.  I get clear video for a few seconds, followed by grey bars. I tried to reinstall it with BARS=0 as your link suggested, but it didn't help.

Still, a few seconds of good video is better than nothing!

Thanks,
Ryan

---

### Post by rmt1947 on 2011-10-24
The grey bars usually mean that the driver is working correctly but can't reliably lock onto the incoming analogue video signal for some reason.  I don't know why this is happening - I have no personal experience of the Wii console and am not sure what kind of output one should expect.  What does the Microsoft Windows driver think the TV standard is?  PAL, NTSC or something else?

Mike

---

### Post by Rybuger1 on 2011-10-28
> **rmt1947 said:**
> The grey bars usually mean that the driver is working correctly but can't reliably lock onto the incoming analogue video signal for some reason.  I don't know why this is happening - I have no personal experience of the Wii console and am not sure what kind of output one should expect.  What does the Microsoft Windows driver think the TV standard is?  PAL, NTSC or something else?

Mike

I don't know how to see what the Windows driver thinks, but the Wii console is NSTC.

Edit: The video feed only shows up on Windows when it's set to NSTC.

Ryan

---

