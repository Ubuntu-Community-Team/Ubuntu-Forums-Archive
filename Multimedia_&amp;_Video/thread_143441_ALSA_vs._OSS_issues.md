---
title: "ALSA vs. OSS issues"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by Ian Maxwell on 2006-03-12
Having just installed Ubuntu the other day, I seem to have a problem with my sound output through drivers other than ALSA. In some programs (Firefox), I can't get any volume but maximum; in others (KBounce, Abuse), I can't get any sound at all. I've been playing around to see what the problem is, and I have gathered some information on exactly what's going on, but none on what to do about it.

The ALSA config shows my audio device as "default". This works just fine. My other two options are "hw:0.0" )CMI9880) and "hw0,1" (CMI9880 Digital). If I switch to the first of these, I get max volume only; if I switch to the second, I get no sound.

OSS config shows my audio device as "Default (CMI9880 (DUPLEX))". If I switch my music player to use OSS instead of ALSA, I get maximum volume or mute, nothing in between.

So, basically, I assume the problem is that stuff not going through ALSA isn't working. Meaning I need to either get OSS working, or find a way to force everything to go through ALSA. I have no idea how to do either; any suggestions?

---

