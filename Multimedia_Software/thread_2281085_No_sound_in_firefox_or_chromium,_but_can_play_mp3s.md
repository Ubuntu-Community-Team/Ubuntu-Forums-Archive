---
title: "No sound in firefox or chromium, but can play mp3s with mplayer"
date: 2015-06-04
forum: Multimedia Software
---

### Post by lewis17112 on 2015-06-04
In both Chromium and Firefox I can *watch* youtube videos, but I have no sound. Soundcloud does not play in either of them.

I can mplay mp3 files fine, but I did have to modify my .asoundrc, as the default soundcard wasn't working.

```

pcm.!default {
    type hw
    card Generic_1
}

ctl.!default {
    type hw
    card Generic_1
}

```

lubuntu-restricted-extras is installed.

Any idea where to proceed from here?

EDIT: for fun I installed pulseaudio. the "stream" of a youtube vid isn't even showing up. I'm perplexed.

---

### Post by Yellow Pasque on 2015-06-04
If you installed pulseaudio, then you need to remove the custom .asoundrc file, because you're bypassing pulseaudio for programs that use libasound (like firefox/chromium).

---

