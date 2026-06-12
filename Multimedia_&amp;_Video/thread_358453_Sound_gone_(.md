---
title: "Sound gone :("
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by lighty14 on 2007-02-10
Well, I'm not sure exactly when this happened (within the last 24 hours or so) but I no longer have sound. Checked to make sure it wasn't muted, have rebooted and stuff.

Oddly enough, the sound control applet in gnome has gone AWOL, as well.

In any case, here's the (relevant) output of lspci:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

It seems independent of the kernel upgrade -- it wasn't working before I upgraded this morning.

And here's lsmod:
```
lsmod | grep snd
snd_hda_intel          20116  0 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

What should I try? It worked fine before -- I think the culprit was attempting to hibernate yesterday.

---

