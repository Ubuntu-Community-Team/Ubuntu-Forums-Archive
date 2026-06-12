---
title: "XVideo corruption"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by Lord C on 2007-12-02
I have VLC player as my default multimedia player.
I'm using GStreamer, as is default with Ubuntu 7.10.
I have the nvidia restricted drivers installed.

For some reason, my playback all started to look like this:
[[IMG]http://img218.imageshack.us/img218/6100/screenshotvlcmediaplayefl1.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshotvlcmediaplayefl1.png)
No matter what player I used.

If I go into settings on VLC or MPlayer or Totem etc and change the video format to X11, playback works fine.
The problem is, X11 video playback is horrible, especially on fullscreen.

"XVideo" in VLC
"Xv" in Xine
Have stopped working.

In mplayer I can use gl2, which looks better than x11 that's for sure.

I don't know what causes this, but it happened before a couple of weeks ago.
Maybe I should remove GStreamer and switch over to Xine?
I really don't want to though. I'd rather solves this problem. My setup was fine.

I have read somewhere that this may be down to Compiz-Fusion?

[Edit]
To my expectance, logging out (or restarting X) did the trick @ fixing this issue temporarily. But i'd like to know what's causing it in the first place.
[/Edit]

Any ideas

---

### Post by acoustibop on 2007-12-03
Certainly, if you're running Compiz, you should disable it for running videos or games, Lord C.

---

### Post by eye208 on 2007-12-03
This is a known issue with the default Nvidia driver included with Ubuntu. It is unrelated to Compiz.

---

### Post by bfoos on 2007-12-03
This is really annoying. I noticed the same issue. Out of nowhere, all video players will start exhibiting the same behaviour as the OP posted. Of course, restarting X or changing your refresh rate will temporarily restore video playback, but that's not really a fix. Oddly enough, when this happens, I've noticed that Gnome Mplayer will render the video properly, while all other players will not. That includes Mplayer. Someone in another thread suggested using Envy to install the latest Nvidia driver, so I gave that a shot. Yey, updated from 100.14.19 to 100.14.23 and videos played like normal. Or so it appeared. About a week later and the problem is back. ](*,) I wish this issue would be resolved, once and for all.

---

### Post by eye208 on 2007-12-04
> **bfoos said:**
> Of course, restarting X or changing your refresh rate will temporarily restore video playback, but that's not really a fix.
Probably the quickest workaround is to press Ctrl-Alt-F1, then Alt-F7. This will switch to a text console and back to X. But yes, it's annoying, and Canonical should put a driver update into the backports repository.

> Oddly enough, when this happens, I've noticed that Gnome Mplayer will render the video properly, while all other players will not.
There are three ways to output video: through XVideo, using OpenGL, or by software rendering (aka. X11). All players can be configured to use X11, but this will make the video look pixelated when scaled. Both MPlayer and VLC can also use OpenGL which is almost as good as XVideo but won't be affected by that driver bug.

---

### Post by bfoos on 2007-12-04
Thanks for your input. For testing I set both Mplayer and Gnome Mplayer to use X11 for video. When the bug crops up, Mplayer won't play video but Gnome Mplayer will. Very odd if you ask me. I've set Mplayer to use opengl. Thanks for the alternative work around.

---

### Post by eye208 on 2007-12-05
> **bfoos said:**
> For testing I set both Mplayer and Gnome Mplayer to use X11 for video. When the bug crops up, Mplayer won't play video but Gnome Mplayer will. Very odd if you ask me.
Yes indeed. "mplayer -vo x11" works well for me every time.

But "mplayer -vo gl2" is better of course.

---

### Post by Selbstmord on 2007-12-08
None of these 'workarounds' fix anything for me, I'm running VLC/various other mediaplayers on a Geforce Go 7600, with restricted nvidia-glx drivers...
I get the borked video on opengl and xv alike. X11 works, but I mean, there must be some other fix for this? What's causing the problem? Can't seem to get any logs or anything that could point to something hardware-wise, I'm guessing it's the driver, and we can all dream on that someones gonna fix it...

It's just a damn shame that every time I'm thinking "they've got it covered now, now's the time to go linux _for real_" and stuff like this ALWAYS turns up (atleast for me). Everybody keeps wondering why everyone don't run linux, I'd say it's more these kind of things than that there's no games... I don't care about games, I just want to be able to play video without having to do workarounds all the time. In some ways, one could say Ubuntu ("with certain hardware" -yeah right, if that counts pretty much anything I've installed it on, which is about 10+ computers all in all) is even more borked than any Windows version could ever be...
Sure, it's the driver, not Ubuntu, yeah right... How come all drivers are like this?

I've got this problem with a USB-interface for recording audio (guitars, to be exact), can't seem to get it working, and nobody else seems to have this particular piece of equipment (IK Multimedia StealthPlug), so if anyone's feeling up for the challenge of getting it working, PM me :)

Aside from everything that's wrong about Ubuntu, everything's great. No really! ;)

---

### Post by ohnoitspaul on 2007-12-09
I have a similar problem, maybe the same one with different symptoms.

Out of nowhere all video playback is in Black&White in both players - VLC and Totem.  Strangely if I leave it running B&W and start another instance of the player it plays perfectly, but only if the first is actually running, if it's stopped or even paused then the second is B&W too.

What really hurts is that as a near newbie - only a couple of months on Linux - I don't even know how to start investigating the problem.

---

### Post by crjackson on 2007-12-14
I have the same issue and I've been searching high/low for a fix.  If you find the proper solutionj please post is here.

Here is a link to my thread [http://ubuntuforums.org/showthread.php?t=640675]("http://ubuntuforums.org/showthread.php?t=640675")

---

### Post by SpaceFarm on 2007-12-15
Video support in Ubuntu is really disappointing.

 This is a pretty basic operation for an OS to do! I know I'm complaining but it's very frustrating having to restart your OS just to watch a video...

---

### Post by crjackson on 2007-12-15
Okay, I have found that I can get it working with CTRL+ALT+BACKSPACE. If I turn OFF desktop effects, the problem is back. I then C+A+B and it fixes it now. If I turn ON desktop effects the problem comes back again, and CAB fixes this too.

Since I've been playing with desktop effects a lot, I guess this has been my problem. Now, I just wonder how long it will work correctly if I make NO more changes. If it continues to work properly, I guess the fix is to ALWAY C+A+B after making changes related to desktop effects. I could live with that. Only time will tell...

---

### Post by cybernytrix on 2008-01-25
Yet another setting you can tweak (for gstreamer/totem) is via the gstreamer-properties program.
Try choosing Video->Xv->Video Texture
or 
Video->Xv->Video Blitter

Yet another option that were discussed on various forms is to simply get the gstreamer0-10-gl package.

Then you can choose "custom" in gstreamer-properties. Type glimagesink.
This seems to crash for me though.

Nvidia needs to get it's act together. ATI/AMD has already released their specs to the community so within a year we will have OSS GL capable ATI driver! Wakeup!

---

