---
title: "Video skips"
date: 2009-03-22
forum: Mythbuntu
---

### Post by itlarson on 2009-03-22
I am getting periodic skipping during playback of broadcast HDTV.  Although it is watchable, I would like to reduce it if possible.  Futzing with interlace and other video playback settings seems to have little effect.  The cpu runs at about 90% mythfrontend, 30% xorg for 720p playback.  Reverse the numbers for 1080i playback.  That's using greedy highmotion.  Turning the deintrelace off reduces 1080i cpu demand, but not the skipping.  Any Ideas?

---

### Post by itlarson on 2009-03-23
Anyone?

---

### Post by newlinux on 2009-03-23
tell us what playback settings you are using (and have tried), and maybe post your frontend logs. Might even be some xorg.conf tweaks that can help. Nothing comes to mind immediately, as various "skips" can be caused by a ton of things. Could be audio problems too. Try turning aggressive audio buffering on.

could you define the type of skipping you get? Are they pauses and starts, or is it skipping a second or two or...

---

### Post by theophile on 2009-03-23
Your IGP supports VDPAU. Use the VDPAU branch and kiss skipping goodbye. :D

---

### Post by newlinux on 2009-03-23
> **theophile said:**
> Your IGP supports VDPAU. Use the VDPAU branch and kiss skipping goodbye. :D

If the problem is CPU usage, yes, but that proc should have no problems with mpeg-2 HD content. And the problem could be audio settings - depends on what the "skips" really are.

---

### Post by itlarson on 2009-03-24
Thank for the replies.  The skipping is like a sudden jump forward of about a second in the video.  The sound is not affected.  When I get home I will post the settings and try the sound thing.

---

### Post by nickrout on 2009-03-24
you will just be guessing at the casue until you look at your mythfrontend log (located in /var/log/mythtv/ )

---

### Post by itlarson on 2009-03-24
I am using:
standard decoder 
2 cpus
no loopfilter
xv-blit renderer
greedy highmotion deinterlace

setting deinterlace to none didn't help much (if at all), so I am just using what looks good.  I will take a look at the logs.

---

### Post by itlarson on 2009-03-24
It seems better now- maybe the aggressive sound buffering helps.  Nothing in the logs stands out.  I'll have to get back to this tomorrow.

---

### Post by itlarson on 2009-03-25
To update this thread- the aggressive sound card buffering seems to have mostly elminated the skipping.  Hopefully it won't come back.  if it doesn't for a week or so I will mark this solved so it can help others.

---

### Post by itlarson on 2009-03-27
Nope- that didn't do it.  The skipping came back.  Can anyone suggest xorg tweaks to try?

---

### Post by newlinux on 2009-03-27
I suggest turning up the verbosity in your frontend logs and looking at that... You can also check to see if it happens when you playback the same recordings with other player, like mplayer. do the skips happen in the same places all the time in the files, or at random meaning if you rewind, does it skip in the same place.

---

### Post by itlarson on 2009-03-27
No- it's random.  Sometimes it goes away altogether.  Lost played perfectly Wednesday, Life on Mars (the show following it) skipped quite a bit Thursday.  How do I adjust the verbosity?

---

### Post by newlinux on 2009-03-27
```
mythfrontend -v help
```

I recommend mythfrontend -v playback

How do these recordings playback with mplayer? Playing this files with another application will help pin down if it is a myth configuration problem or not.

---

### Post by itlarson on 2009-03-28
Here's output from "mythtv -v playback"

[CODE]2009-03-28 21:37:37.602 NVP: Video is 4.55751 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.602 NVP: Video is 4.48205 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.603 NVP: Video is 4.17071 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.603 NVP: Video is 3.68249 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.603 NVP: Video is 3.07655 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.756 NVP: Video is 3.84116 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.756 NVP: Video is 4.22952 frames behind audio (too slow), dropping frame to catch up.
2009-03-28 21:37:37.756 NVP: Video is 4.281 frames behind audio (too slow), dropping frame to catch up.[CODE]

What do I do next?

---

### Post by newlinux on 2009-03-28
do you have use video as a timebase set? If so, disable it.

---

### Post by itlarson on 2009-03-28
When I use mplayer, the audio lags the video substantially.

---

### Post by newlinux on 2009-03-28
did you try my previous suggestion? Also I wasn't completely clear about my previous audio suggestion. There are two "buffering" options. One is in the General Settings, the other in the Playback settings (under TV settings). the one in General settings-> "Aggressive Sound card buffering" or some sort you might want turn off. Exta audio buffering (the one in Playback) is the one I mean to refer to that you would want to turn on.

---

### Post by itlarson on 2009-03-29
Video as timebase is off.  Swithched the buffering in "general" off, and the one in "tv settings" on.  No difference.  I used to have a mythbox with a single core athlon 2100mhz and it didn't skip like this unless you used the best de-interlace.  This one skips even if you turn the de-interlace off.

---

### Post by newlinux on 2009-03-29
yeah doubt it is a CPU issue. I'm inclined to believe it is a playback profile issue. You didn't post enough your log to really analyze properly. you mentioned your primarily deinterlacer is greedy high motion, what's your secondary (which is what would be used if greedy high motion isn't working - which I can't know based on the part of the logs you showed). I'd try using one field for your secondary, and trying different primary ones and different playback profile settings to see if you can get it to work.


Does this happen on all HD playback or on certain channels or programs?

---

