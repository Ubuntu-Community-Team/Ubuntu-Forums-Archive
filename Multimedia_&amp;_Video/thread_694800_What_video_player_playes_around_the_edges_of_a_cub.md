---
title: "What video player playes around the edges of a cube?"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by PiggiePaul on 2008-02-12
Just installed Ubuntu so I'm just using "what it came with" re media players. (Totem 2.2)

On a YouTube demo of Compiz Fusion (with the cube) I saw a video playing even when half of it was wrapped around the sides of the cube and the cube moved away in the distance.

Totem does not do this, and just displays a blank screen while viewing the 3D desktop cube.

Anyone know what video player they have have been using.

also (on the same subject) if there a better video file player to use than Totem?

I have an AVI file of a HD recording and Totem won't play it.
(It plays most other stuff though)


Thanks

---

### Post by mad_max0204 on 2008-02-12
Mplayer

Works fine with Desktop Qbe

---

### Post by Keith Hedger on 2008-02-12
sorry accidently posted the wrong thing.
I think you need the video plugin enabled

---

### Post by PiggiePaul on 2008-02-12
> **mad_max0204 said:**
> Mplayer

Works fine with Desktop Qbe

thanks.
Is MPlayer better than Totem as a default player?

Is there a easy way to try it out?

---

### Post by PiggiePaul on 2008-02-12
> **Keith Hedger said:**
> sorry accidently posted the wrong thing.
I think you need the video plugin enabled

Thanks.
Could you explain a little further?

---

### Post by themusicwave on 2008-02-12
Under Compiz Settings

System -> Preferences -> CompizConfig Setting Manager

 Check the video playback box in the Utility section

That will at least turn the plugin on

---

### Post by CarpKing on 2008-02-13
I think you have to patch MPlayer for this to work.  There are some debs (download and click to install) of the patched version floating around, but I don't know where.

---

### Post by mad_max0204 on 2008-02-13
No need for patch. I installed it from a guide on this forum, plays good and works with compiz.

---

### Post by x-dragon on 2008-02-13
VLC can help 2, you might wanna try that too...

---

### Post by PiggiePaul on 2008-02-13
Thanks for the advice.

This is (however) the one annoyance (confusion?) for someone like myself (Complete Newbie)

It seems hard work to get to find out what versions of what software are the best to run.

Common sence would tell me (if I was putting together a Linux Distro) that I'd pick the cream of all the apps and bundle them in with the Linux install by default.

(I'm assuming that's what they TRY and do)

But sometimes it seems like it's not the case, and you have to come on forums asking what's the best this, what's the best that for every single app.

Does make it very confusing, and thanks to all of you for helping us newbies out.

It must get very repetative to keep being asked what's the best program to play music, what's the best to play video, what's the best everything else.

I know I've got a LOT more to ask yet ;)

So. Again, thanks to you all for putting up with the same questions all the time

---

### Post by vikrant82 on 2008-02-13
Smplayer does that for me !.. Uses mplayer as backend...

---

### Post by eye208 on 2008-02-13
Any player can do this if you configure it to use X11 output (i.e. software rendering).

Totem: Run "gstreamer-properties" and select video output "X Window System (No Xv)".

MPlayer: Use the option "-vo x11".

VLC: Set video output module "X11" in preferences.

---

### Post by PiggiePaul on 2008-02-13
> **eye208 said:**
> Any player can do this if you configure it to use X11 output (i.e. software rendering).

Totem: Run "gstreamer-properties" and select video output "X Window System (No Xv)".

MPlayer: Use the option "-vo x11".

VLC: Set video output module "X11" in preferences.


Thanks for that piece of information.

Do I however take it that there are good reasons why you would not want to us X11 software rendering? 

Performance, speed, stalility?

---

### Post by eye208 on 2008-02-13
> **PiggiePaul said:**
> Do I however take it that there are good reasons why you would not want to us X11 software rendering? 

Performance, speed, stalility?
The bad thing about software rendering is the lack of anti-aliasing. If you scale the video to any size other than the original one, you will see pixelation.

---

