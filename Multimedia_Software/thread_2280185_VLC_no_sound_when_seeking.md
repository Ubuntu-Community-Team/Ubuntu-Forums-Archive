---
title: "VLC no sound when seeking"
date: 2015-05-28
forum: Multimedia Software
---

### Post by kerryhall on 2015-05-28
Hi folks,

I've noticed a problem with VLC, with certain media only. When trying to seek, there is a large amount of lag (several seconds) and when it finally catches up, there is no sound. Seeking a bit more randomly causes the sound to return.

Thanks!!

---

### Post by monkeybrain20122 on 2015-05-28
Usually happens only with hd videos. DVD quality is fine here. But not all hd videos have the problem. It sort of works, but not reliably.

It has been a recurring bug for years if you check the videolan forums. I don't think there is any fix (despite claims from time to time that it was fixed in version x, but it never works reliably here, I have tried both release and development versions)


A workaround would be, after seeking disable and then re-enable audio. Or better, use Smplayer.

---

### Post by Rob Sayer on 2015-05-29
Actually that happens sometimes in smplayer too.

I think it's usually either crap 3rd party codec packs on the windoze box used to encode the video, or it was just done by someone who doesn't know how to use a video encoder properly.  Though video encoding *is* pretty complex ...

---

### Post by monkeybrain20122 on 2015-05-29
> **Rob Sayer said:**
> Actually that happens sometimes in smplayer too.
.

Maybe it depends on what backend you use for Smplayer. I never experienced that using either mplayer2 or mpv.

---

### Post by kerryhall on 2015-05-31
So, if the video wasn't encoded properly, is that something we can check?

---

### Post by monkeybrain20122 on 2015-06-01
> **kerryhall said:**
> So, if the video wasn't encoded properly, is that something we can check?

It may be that some videos are not encoded properly, but I doubt that it is the main reason why vlc' seeking is broken. Seeking works properly with Smplayer and mpv for the same videos even when it doesn't work with vlc.

---

