---
title: "Sound recording intermittent"
date: 2015-11-29
forum: Multimedia Software
---

### Post by SimonHGR on 2015-11-29
Hi all,

I've been doing screen capture successfully for a while using avconv, however, today I notice that when I try to get audio from the monitor of analog stereo output, it's intermittent. I used to get solid sound, but now I get approximately a second of sound, then a second of silence, then a second of sound, and so on.

I'm pretty sure I've installed nothing but standard system patches, and the normal playback is fine. Video capture is running along smoothly. It's just the sound that comes and goes.

I don't know if the period of sound / no-sound is exactly consistent, nor exactly one second, but that captures the effect in a qualitative description.

Any thoughts? Why might this have changed suddenly? I think I last used this perhaps a couple of weeks ago, give or take. Oh, and there's lots of memory free, lots of CPU free, and I tried, in the time-honored Seattle tradition, a reboot, just in case :)

TIA...

---

### Post by SimonHGR on 2015-11-29
Actually, I lie... I'm not using avconv, I'm using ffmpeg.. I switched and built this into a script some time ago. Not sure if it makes any difference though.

---

### Post by SimonHGR on 2015-11-29
Hmm, well, I guess there's a workaround. It seems that avconv is still working correctly. I forget why I changed to ffmpeg, but it wasn't primarily for use during captures, it was something else. So, if anyone knows what happened to ffmpeg, I'd be please to fix the issue with it; but in the meantime, I guess I have my solution: use avconv instead.

---

