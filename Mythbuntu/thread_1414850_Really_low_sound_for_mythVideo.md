---
title: "Really low sound for mythVideo"
date: 2010-02-24
forum: Mythbuntu
---

### Post by doug-M on 2010-02-24
I'm using onboard audio to feed a 2.1 analog speaker system on 9.10.
I notice that alsamixer has the master set back at 75-80% after reboot even if I do a:
sudo alsactl store

Some other people mention putting -af volnorm on the mplayer command line but it doesn't seem to do anything for the "Internal" plugin.

So how can I get better volume? Everything is up at 100% and I can barely hear it.

Also how can I make alsamixer keep the master volume up?

I'm using ripped DVDs, don't have any liveTV.

---

### Post by nickrout on 2010-02-24
I am not sure why your settings are not sticking, but the PCM setting in alsamixer is also relevant. Make sure its not down low.

---

### Post by doug-M on 2010-02-26
I have maxed up the PCM volume as well.

It seems that other videos have a decent sound level but ripped DVDs have a really low volume. Perhaps it is the DTS soundtrack? As I said I am only use an analog 2 speaker + sub setup and I really can't hear it.

Is there a way to do volume normalization with the "internal" plugin video player?

---

