---
title: "DV Capture"
date: 2007-07-25
forum: Multimedia Production
---

### Post by thebucksstop on 2007-07-25
OK, thanks to variona, I've got Kino picking up my camera, and playing in nicely.

However, when I checked a sample file, the interlacing is horribly noticeable - horizontal movements leave behind alternate lines on the monitor. Is this an artifact, or is there a workaround? I'm just trying to start editing video on linux at the moment, having messed around a bit with both Avid Xpress and Final Cut Pro in the past, and I didn't have these problems then!

So, does anyone else have this problem? How do I fix it? Ultimately, whilst I don't really want to edit with the footage like that, it is manageable...but not if I'm going to have the same effect with the final product.

Any help much appreciated
C

---

### Post by thebucksstop on 2007-07-26
Nobody got any ideas?

---

### Post by Cryophallion on 2007-07-27
There are a few possible things here, and I will give you options for all of them, as I can't see the video to determine the most likely candidate:

1. Do the alternating lines show up when you are watching the video on the camera itself (these are usually wider lines). If so, then you probably need to clean the heads on the camera. You could buy a tape to do this for you, but that is like taking sandpaper to it. Using a q-tip, and a very small amount of rubbing alcohol, clean the heads all the way around, then let it air dry before putting the tape back in. IF you need more help with that, let me know.

2. Try running a de-interlace filter on the video. Most of the video programs have this, especially avidemux (open video, go to video-filters-interlacing-deinterlace)

3. Try changing to raw or dv1 in kino's capture settings.

4. Try importing the video into another program (kdenlive, etc). Do the lines show up there? If so, how are you connecting the camera to the computer?

P.S. - give us a little time to get back to you... we all want to help, you just have to be patient for someone who knows to hop online.

Welcome to linux production. May I recommend kdenlive (kdenlive) for something a little closer to final cut? Just be aware it is still very much a work in progress, but they have made a very good editor so far.

---

### Post by Rexbron! on 2007-07-27
> **thebucksstop said:**
> Nobody got any ideas?


I could be a number of things, like those above. My guess (if every frame has interlacing artifacts) is that kino is playing the file back in the wrong field order. 

Try playing the footage back in something like mplayer and see if you get the same results.

---

### Post by thebucksstop on 2007-07-29
Thanks for getting back to me guys- I didn't want to be impatient, but I guess I'm more ued to some of the other sections of the forums where, if it doesn't get answered with half an hour, let alone a day, it drops from sight for all eternity unless bumping - bad habit I'll break myself out of!

1) The video's fine on the camera screen, so I don't think it's the heads. Certainly, the camera gets regularly serviced, so that ought not to be a problem, ruling out number this, I think.

2) I played the video back through mplayer with a deinterlace filter, and the artifact went away. I don't know how these filters work though, so I don't know how that affects the actualy video itself. I don't see how these filters will help me when I'm cutting though, as I'll be playing back through the NLE, not kino/mplayer/avidemux. Feel free to prove me wrong though!!

3) I'm importing in RAW .dv at the moment, rather than DV2 .avi - I've got the space to play with, so there's no reason not to as far as I can see.

4) I'll install kdenlive and see how importing through that goes and keep you informed. Just looking at the screenshots on teh web, it certainly looks a LOT friendlier than Cinelerra (which I can hack about in, but it's still really crashy and buggy, particularly the compositor...but that's another story for another day!). Does kdenlive play nicely with GNOME?

Really appreciating the help! :)

---

### Post by jkwarras on 2007-07-30
Your video is interlaced, and it'll look like this on the lcd display. If you want to get ride of this you'll have to deinterlace the footage (several methods but be sure to know that this will always degrade the footage since it's trying to get progressive footage from a interlaced source).

Cinelerra is the closest to a pro nle like FCP or Avid, but yes, it's ugly.

---

