---
title: "Flash hardware acceleration sitrep"
date: 2012-06-22
forum: Multimedia Software
---

### Post by ticket on 2012-06-22
Seems the current status of GPU flash acceleration under Linux is this:
 There isn't any.

If you have an nVidia card, older versions of adobe flash supported hardware acceleration, but this broke with the last (and final) adobe flash plugin update.

If you have ATI, flash hardware acceleration was never supported.

So it appears that if you want to play full screen flash video on a Linux box, you have to use software rendering, which means using a beefy, modern CPU.

If you have an old CPU, it is no longer possible to run full screen flash under linux, unless you like slideshows.

Have I got that right?

---

### Post by brainwash on 2012-06-22
Kinda old story, but yeah, Adobe is not able to support accelerated flash video decoding on Linux systems. However, my 6 year old CPU is still able to play full screen flash videos (720p) without stuttering.

---

### Post by ticket on 2012-06-22
That's good! 

I have a spare PC, a 1.5Ghz pentium 4, with AGP, and full screen flash at 720p is a slide show.

Can you say what CPU you have?

---

### Post by brainwash on 2012-06-22
Intel Pentium D 930  (3.00 GHz)

So your CPU is even older than mine. In this case you should definitely try the Firefox addon [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), which may help improve the playback of flash videos on your system by using a standalone player like MPlayer instead of Adobe's Flash Player.

---

### Post by firekage on 2012-06-22
> **brainwash said:**
> Intel Pentium D 930  (3.00 GHz)

So your CPU is even older than mine. In this case you should definitely try the Firefox addon [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), which may help improve the playback of flash videos on your system by using a standalone player like MPlayer instead of Adobe's Flash Player.

Can you tell more about playing movies, for an example, from youtube by this addons? It will be played in web browser or it will open player for it?

I'm asking because after upgrading FF from 7.0 to 13.0 and reverting back i don't have the same flashplugin that i have - i have newer and i regret having it but i can't install/find the old one from ubuntu 11.10 repos.

---

