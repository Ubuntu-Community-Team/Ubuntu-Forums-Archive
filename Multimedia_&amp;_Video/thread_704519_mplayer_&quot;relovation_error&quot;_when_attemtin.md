---
title: "mplayer &quot;relovation error&quot; when attemting to play through hwac3 or hwdts"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by peterdm on 2008-02-22
Because I had trouble with pcm output over spdif, I followed [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") wiki and recompiled alsa 1.0.16 (driver, lib and utils).
Unfortunately, hwdts and hwac3 are now broken (they worked before I recompiled).

Whenever I attempt to play with mplayer like so

```

mplayer -ao alsa:device=spdif -ac hwac3 dolbyrain.vob

```

mplayer exits and the last couple of lines look suspicious:

```

mplayer: relocation error: mplayer: symbol snd_config_search_alias_hooks, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

```

What does it mean?
How can I fix this?

---

