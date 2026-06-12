---
title: "Choppy sound and video playback + libasound2 + alsa+pulseaudio problem"
date: 2012-02-11
forum: Multimedia Software
---

### Post by swizzla on 2012-02-11
Hi,
I've been using ubuntu on my laptop (gateway nv53) for a year now, and never experienced this issue in any of the releases and sound/video worked flawlessly in Oneiric until now. For reasons unknown to me, a few days ago the sound/video playback became very choppy. I've tried reinstalling alsa and pulseaudio and gstreamer several times, it worked once but soon started again when lmms or other audio software was run. Next thing I did was install the alsa ppa to get the latest alsa drivers. That didnt work.

It's not a sound card problem because it worked fine before.

I did just about everything I could find for solutions online.

Something I noticed when trying to reinstall libasound2 and other alsa components was this:

 E: Internal Error, No file name for libasound2

That message shows up whenever I try to reinstall that library.

I cant purge and reinstall it because too many thing depend on it and would have to be removed... basically everything that plays sounds.


libasound never gets reinstalled, so does this have anything to do with the choppy sound problem?

Has anyone experienced this or have any idea how to fix the choppy sound issue?

Thanks

---

