---
title: "How do I change the default video codec an app uses?"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by jonno on 2007-11-27
I have had problems with a grid of dots appearing on my videos with all applications ever since I started with Ubuntu (7.04, now 7.10).

[This fix]("http://ubuntuforums.org/showpost.php?p=2896078&postcount=2") (changing the video output module) seems to have worked for most applications such as Gstreamer, , Totem, VLC & Xine (but strangely that didn't fix gxine).

However now I'm trying to use the new beta Skype with video but of course when I test the video in Skype the grid shows up again.

I am trying to understand what is going on here. I admit to not really understanding how the fix above worked. It seems like a different setting is required for each player. Can't I just delete the offending driver or codec so that the default switches to the one that works? For that matter are we talking about an offending driver or is it a codec?

Or does anyone know how I can check/change which driver/codec skype is using?

Any help appreciated,

Jonno.

---

### Post by jonno on 2007-11-28
Here is the response I got from one of the Skype developers to the same question over in the Skype forum:
"The solutions in that thread [this one] seemed to involve using something other than Xv for video overlay. Unfortunately, Skype currently -only- supports Xv overlay, so if your Xv overlay is faulty, there's no solution at the moment.

It may be better to encourage driver developers to get to the bottom of the problem and fix or workaround where possible."

So I guess my problem is with the Xv driver/overlay. Can anyone help me figure out what is wrong on my system? What do I need to look at? I'm not even sure how to find out what video card I have or what driver it is using.

---

### Post by jonno on 2007-11-28
If it helps I have a Dell Optiplex GX260 and the video is integrated (Intel 845G chip). Don't know how to check what drivers Ubuntu is using.

---

### Post by jonno on 2007-11-28
Ok I looked at my xorg.conf and here is the info on the video:
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Not sure if there is anything useful in the file.

---

### Post by jonno on 2007-11-28
Just spotted [another thread]("http://ubuntuforums.org/showthread.php?t=585729") where someone had the same issue with the same chipset.

So I'm thinking this is a Intel 82845G/GL chipset/Xv overlay conflict.

I don't have Compiz installed either.

---

### Post by disturbedite on 2007-11-28
with smplayer you can choose the audio & video drivers as well as the decoders/demuxers.

---

### Post by jonno on 2007-11-30
Ok I found a[ bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146728") that seems to be the same issue.
Someone had found that the grid went away when changing the video depth from 16bit to 24bit. I tried it and it worked! So the problem seems to be a conflict with a combination of the  i810 driver, Xv overlay and 16 bit video depth.

Anyone know how setting my video depth to 24 bit might affect my performance?

---

### Post by jonno on 2007-11-30
Update: 
I did find [this article](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e) on a newer Intel driver but the grid was still there when using 16 bit depth.

---

