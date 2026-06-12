---
title: "[SOLVED] No sound in Totem"
date: 2008-06-25
forum: Multimedia Software
---

### Post by thezood on 2008-06-25
I'm having a problem with Totem. I recently wanted to get DVD playback working, so I installed quite a lot of gstreamer plugins. The problem is, now Totem has no sound whatsoever. Even the options of changing sound volume is greyed out in the program.

I tried reinstalling both Totem and all the gstreamer stuff I could remove without removing ubuntu-desktop and other packages that seem to be good to have. :)

Does anyone know what this could be?

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Try setting totem to use ALSA sound driver.

Unless if this is a codec conflict issue... well... then you need get rid of totem and its codecs for your w32 and xine codecs sake. At least it worked for me, when I had such codec issues with totem. Good luck!

---

### Post by thezood on 2008-07-07
> **Odrodzona-Sarmacja said:**
> Try setting totem to use ALSA sound driver.

Unless if this is a codec conflict issue... well... then you need get rid of totem and its codecs for your w32 and xine codecs sake. At least it worked for me, when I had such codec issues with totem. Good luck!

Thanks for the response. I the more violent approach - I completely removed all codecs, players and media libs and installed them anew. Then it worked. :)

---

