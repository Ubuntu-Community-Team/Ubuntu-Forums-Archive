---
title: "My Big List of Linux Video Issues"
date: 2009-08-29
forum: Multimedia Software
---

### Post by Grimhound on 2009-08-29
I've spent several occasions coming back to Ubuntu since the Gutsy era trying to get things to run properly on my computers. Below is a video-related list of issues I have with Ubuntu as it stands currently in 9.04.


-The desktop flickers through the video when playing video at fullscreen.
-Totem stutters and chokes when told to play a DVD, playing what it does at 1/100 speed.
-Flash stutters, locks up, and uses 60% of the CPU resources to play in a 200x300 box.
-Flash completely dies when played fullscreen.
-The system audio freezes at full volume in the fashion of a critical driver failure when Flash chokes.
-Flash has not been significantly improved in its performance since Gutsy from what I've noticed. The same issues for the most part persevere.

The inability of Linux to ably play video and make use of Flash are the main reasons I keep going back to Windows within days of attempting to use it. Sacrificing my hardware just to use Linux just isn't worth it.

---

### Post by yabbadabbadont on 2009-08-29
All flash related issues should be taken up directly with Adobe.  Neither Ubuntu, nor any other linux distribution, have any control over the quality of the flash plugin as provided by Adobe.

You desktop flicker issue is probably related to compiz (i.e. desktop effects).  Try disabling all desktop effects and see if it corrects the issue.

Totem pretty much stinks (in my opinion).  Try using something like vlc or mplayer to play the DVD and see if it helps.

These last two suggestions will at least help narrow down where the issue lies.  (underpowered hardware or software issues)

---

### Post by jpeddicord on 2009-08-29
Should I move this to Testimonials then? Doesn't seem like you're asking for help. You didn't even tell us what your video card is.

---

### Post by Grimhound on 2009-08-29
> **yabbadabbadont said:**
> All flash related issues should be taken up directly with Adobe.  Neither Ubuntu, nor any other linux distribution, have any control over the quality of the flash plugin as provided by Adobe.

You desktop flicker issue is probably related to compiz (i.e. desktop effects).  Try disabling all desktop effects and see if it corrects the issue.

Totem pretty much stinks (in my opinion).  Try using something like vlc or mplayer to play the DVD and see if it helps.

These last two suggestions will at least help narrow down where the issue lies.  (underpowered hardware or software issues)

I'm running an Intel X3100 integrated chip, and the issues have persisted even with Visual Effects off when using VLC. It's mind-numbing.

---

### Post by yabbadabbadont on 2009-08-29
Integrated Intel video...  sounds like underpowered hardware to me.

(Or else it isn't being configured properly for DRI for some reason)

---

### Post by Grimhound on 2009-08-29
> **yabbadabbadont said:**
> Integrated Intel video...  sounds like underpowered hardware to me.

To run flash videos and movies that run perfectly fine under Windows 7?

---

### Post by yabbadabbadont on 2009-08-29
> **Grimhound said:**
> To run flash videos and movies that run perfectly fine under Windows 7?

See my first point about Adobe...

---

### Post by Grimhound on 2009-08-29
> **yabbadabbadont said:**
> See my first point about Adobe...

As for VLC and Mplayer. Every time I attempt to maximize or go to a DVD menu, the programs crash. It's just frustrating to no end. Sorry to come off as whining.

---

### Post by jpeddicord on 2009-08-29
Run and paste results:
```
glxinfo | grep direct
```


...and in the middle of writing this I've realized something. Jaunty has issues with Intel graphics when using EXA mode (the default).

You may want to take a peek at this sticky; it will solve the issues for now.
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

The real fix comes in Karmic (9.10) in October.

---

### Post by Grimhound on 2009-08-29
> **jacobmp92 said:**
> Run and paste results:
```
glxinfo | grep direct
```


direct rendering: Yes

---

### Post by jpeddicord on 2009-08-29
> **Grimhound said:**
> direct rendering: Yes

Yeah, it's likely the EXA issue I linked above. Follow the instructions there and you should be set. I share your frustration with the terrible Intel performance on 9.04; thankfully it is fixed in Karmic.

---

### Post by Grimhound on 2009-08-29
> **jacobmp92 said:**
> Yeah, it's likely the EXA issue I linked above. Follow the instructions there and you should be set. I share your frustration with the terrible Intel performance on 9.04; thankfully it is fixed in Karmic.
I updated the kernel yesterday, but had to reformat to the standard again after it became apparent I would never get the Broadcom STA driver Ubuntu gave me upon initial installation reinstalled. I'm not some Linux savant and I couldn't understand the instructions.

---

### Post by sloggerkhan on 2009-08-29
> **Grimhound said:**
> I've spent several occasions coming back to Ubuntu since the Gutsy era trying to get things to run properly on my computers. Below is a video-related list of issues I have with Ubuntu as it stands currently in 9.04.


-The desktop flickers through the video when playing video at fullscreen.
-Totem stutters and chokes when told to play a DVD, playing what it does at 1/100 speed.
-Flash stutters, locks up, and uses 60% of the CPU resources to play in a 200x300 box.
-Flash completely dies when played fullscreen.
-The system audio freezes at full volume in the fashion of a critical driver failure when Flash chokes.
-Flash has not been significantly improved in its performance since Gutsy from what I've noticed. The same issues for the most part persevere.

The inability of Linux to ably play video and make use of Flash are the main reasons I keep going back to Windows within days of attempting to use it. Sacrificing my hardware just to use Linux just isn't worth it.

Your issues all sound like you have a bad graphics driver/chipset than anything to do with linux quality overall.

---

### Post by Grimhound on 2009-08-29
> **sloggerkhan said:**
> Your issues all sound like you have a bad graphics driver/chipset than anything to do with linux quality overall.

There's a nice formal bug report over the flash issues that was submitted to Adobe. I'm curious if they'll ever respond to it. Quite a few people backing it.

---

### Post by sloggerkhan on 2009-08-30
> **Grimhound said:**
> There's a nice formal bug report over the flash issues that was submitted to Adobe. I'm curious if they'll ever respond to it. Quite a few people backing it.

I used to have issues with flash, but ever since adobe's been offering debs on their own website it's been working fine. Only issue I have anymore is some screen tearing on full screen.

---

