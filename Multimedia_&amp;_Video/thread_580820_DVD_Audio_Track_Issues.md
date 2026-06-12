---
title: "DVD Audio Track Issues"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by climber117 on 2007-10-19
After upgrading to Gutsy, I couldn't play DVDs at all. By adding the Medibuntu repositories, I managed to get video playback in both Totem and VLC. I took the following actions to get video playback:
- Installed non-free-codecs
- Installed libdvdcss2
- Installed w32codecs
- Switched from totem-gstreamer to totem-xine

However, I get no sound at all in VLC. In Totem, something even stranger happens. The background sound (music, sound effects, even voices peripheral to the main conversation) is there, but the default audio track for voices does not play at all. On DVDs with multiple languages or commentaries, the alternate languages and commentaries work, but the default language does not. On DVDs with only one language track, I get no voice at all.

So for example, my copy of Hotel Rwanda has three audio tracks (listed as Sound -> Languages), which are English, French, and English 1 (a commentary). Both the French and English 1 tracks work, but the default English track does not.

My copy of Gladiator has only one language track, and I get no voices no matter what I do.

I've tried this on multiple drives with multiple DVDs, all with the same result. Any ideas how to fix this?

Thanks in advance for your help.

---

