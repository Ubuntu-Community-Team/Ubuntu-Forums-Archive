---
title: "XVID Download?"
date: 2011-07-16
forum: Multimedia Software
---

### Post by Partian on 2011-07-16
Hey guys,
I watch alot of shows on the internet
and most websites need xvid to watch the episode
is their any way to get xvid for Linux?

---

### Post by handy on 2011-07-16
These two links will hopefully sort you out:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

---

### Post by andrew.46 on 2011-07-17
> **Partian said:**
> I watch alot of shows on the internet
and most websites need xvid to watch the episode
is their any way to get xvid for Linux?

By default MPlayer uses libavcodec's *ffodivx* to playback xvid video so for MPlayer, SMPlayer and UMPlayer you will not need to download any extra codecs at all. vlc also uses avcodec for xvid playback. Mind you my own copy of MPlayer is also compiled against libxvidcore 1.2.2 and playback is actually better using the *external* library :(.

---

