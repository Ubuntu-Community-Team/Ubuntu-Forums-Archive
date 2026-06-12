---
title: "VLC - No interface after upgrading to 1.0 on 64-bit system."
date: 2009-07-13
forum: Multimedia Software
---

### Post by u-slayer on 2009-07-13
I just upgraded vlc to 1.0 and now I can't see the interface to control the video. It just plays in a window by itself. VLC 1.0 works fine on my 32-bit laptop. Pls help.

```
vlc '/x/newmkv/DRAGON_SLAYER.1247424728.mkv' 
VLC media player 1.0.0 Goldeneye
Remote control interface initialized. Type `help' for help.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x7fbcd4004d38] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x7fbcd4004d38] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x7fbcd4004d38] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[0x1655918] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)

```

---

### Post by mc4man on 2009-07-13
try opening vlc once like this to reset to default interface (should be qt4

```
vlc --reset-config --reset-plugins-cache
```

---

### Post by u-slayer on 2009-07-13
> **mc4man said:**
> try opening vlc once like this to reset to default interface (should be qt4

```
vlc --reset-config --reset-plugins-cache
```

Thank a lot! That fixed it:p

---

