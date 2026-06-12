---
title: "Totem not syncing some .wmv files"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-11-14
Hi all,
I'm getting a really annoying problem. I've installed all the possible multimedia codecs through Automatix, and most of the times I can play anything with no problem. But at times, when I try to play some .wmv files, audio and video do not sync.

Anyone with a suggestion?

Thanks for your time!

---

### Post by William the Conquerer on 2006-11-14
well, ok, so first off.  Did you install xine from automatix?  Totem is really just a frontend to either gstreamer or xine, the multimedia "engines."  That means gstreamer (which comes by default with edgy) is unable to correctly decode the wmv video and audio OR, xine isn't able to (IF you installed it through automatix).  I'll tell you now wmv's are a PAIN IN THE *** in linux...  they're a proprietary format created by microsoft, so it's not really that surprising they don't work 100%.  I am running xine as the backend to totem and I can play wmv files fine... If you're running gstreamer you could switch over to xine or vice versa.  Otherwise, you COULD look into reencoding these files to another format like xvid or something...  Hope that helps.

---

### Post by justinjstark on 2006-11-14
> **finferflu said:**
> Hi all,
I'm getting a really annoying problem. I've installed all the possible multimedia codecs through Automatix, and most of the times I can play anything with no problem. But at times, when I try to play some .wmv files, audio and video do not sync.

Anyone with a suggestion?

Thanks for your time!

Are you using totem?  Default totem with the gstreamer backend still has some problems that will be ironed out by the next ubuntu release.  For now, try using totem-xine instead of totem-gstreamer.  I find that it fixes all of my playback problems.

---

