---
title: "What's the best video output driver to use with an Ivybridge HD4000 graphics card?"
date: 2013-02-26
forum: Multimedia Software
---

### Post by dreamkatcha on 2013-02-26
Hi,

I've been using SMPlayer to play an assortment of movie files and am finding that they either freeze sporadically or the video tears with the smallest of camera movements. Are there any settings that compliment my video card particularly well?

---

### Post by Yellow Pasque on 2013-02-26
VA-API is best for Intel GPU's, but mplayer doesn't have va-api output by default (there's a special va-api version).

Have you tried VLC?

---

### Post by dreamkatcha on 2013-02-27
Thanks for the tip. I'll do some research and see if there's a plugin I can use.

I've also got VLC installed, but don't like using it for two reasons; there's no quick way to expand the window to fill the screen, and it doesn't remember your playback position. Other than that it's the much more reliable, and compatible choice, albeit with too many options for its own good.

Update: I followed the instructions [here]("http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html") and it now works perfectly. All the glitchy tearing I was experiencing has vanished, even when watching fast-paced action sequences. Thanks again! :)

---

### Post by Yellow Pasque on 2013-02-27
You're welcome. VA-API is the main reason I recommend Intel graphics to non-gamers nowadays. Please mark the thread solved (thread tools menu towards the top).

---

### Post by dreamkatcha on 2013-02-28
Just tried marking it as solved, but I don't appear to have that option available to me, sorry.

---

### Post by Yellow Pasque on 2013-02-28
Hmm.. an issue with the new interface? You do see the thread tools menu, correct?

---

### Post by Rebelli0us on 2013-03-01
Video tearing that you see when panning the camera is probably due to the player, not the driver.

Here's what I have, no problems at all.

-Display-
Resolution		: 1920x1080 pixels
Vendor		: The X.Org Foundation
Version		: 1.11.3
-Monitors-
Monitor 0		: 1920x1080 pixels
-OpenGL-
Vendor		: Tungsten Graphics, Inc
Renderer		: Mesa DRI Intel(R) Ivybridge Desktop 
Version		: 3.0 Mesa 8.0.4
Direct Rendering		: Yes

---

### Post by dreamkatcha on 2013-03-01
Yes, I can see the 'thread tools' drop-down menu, but the only options available are:-

Show printable version
Email this page
Subscribe to this thread

Interesting. Which player are you using Rebelli0us? SMPlayer does[COLOR=#000000] seem to become a bit flakey at times compared to VLC. I tried watching an H.264 video earlier using the VA-API output driver and it was unwatchable due to all the stuttering and freezing frames. I switched back to XV and it was much smoother, though the tearing was back with a vengeance.

Is enabling post-processing a good idea? What about the quality setting? Increasing the cache size and numbers of threads for decoding doesn't seem to help.[/COLOR]

---

### Post by Yellow Pasque on 2013-03-01
> Yes, I can see the 'thread tools' drop-down menu, but the only options available are..

Okay, it's a known issue. [http://ubuntuforums.org/showthread.php?t=2120972](http://ubuntuforums.org/showthread.php?t=2120972)

> I switched back to XV and it was much smoother, though the tearing was back with a vengeance.

IIRC, Xv can't do video sync (vsync), hence the tearing.

---

### Post by Rebelli0us on 2013-03-02
> **dreamkatcha said:**
> Yes, I can see the 'thread tools' drop-down menu, but the only options available are:-

Show printable version
Email this page
Subscribe to this thread

Interesting. Which player are you using Rebelli0us? SMPlayer does[COLOR=#000000] seem to become a bit flakey at times compared to VLC. I tried watching an H.264 video earlier using the VA-API output driver and it was unwatchable due to all the stuttering and freezing frames. I switched back to XV and it was much smoother, though the tearing was back with a vengeance.

Is enabling post-processing a good idea? What about the quality setting? Increasing the cache size and numbers of threads for decoding doesn't seem to help.[/COLOR]


I use VLC. I see the tearing in my own videos when I pan the camera horizontally. You can fix that in >  Preferences > Video > **Output** method.

---

### Post by dreamkatcha on 2013-03-05
Good to know, thanks.

Well SMPlayer seems to go from bad to worse. Now the audio/video is out of sync on everything I play, and the auto-sync option does nothing to fix it. I wonder if there's a 'best' audio output driver to use to eliminate this issue.

---

