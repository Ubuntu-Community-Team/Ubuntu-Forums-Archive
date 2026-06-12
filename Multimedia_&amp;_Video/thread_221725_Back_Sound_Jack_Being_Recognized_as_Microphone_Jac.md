---
title: "Back Sound Jack Being Recognized as Microphone Jack"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by Turkey Pwner on 2006-07-23
Hello.  When I first installed Ubuntu Dapper Drake, my sound had no problems.  But recently, the sound jack at the back of the computer is being recognized as a microphone jack. (I know this because there is no sound coming through my speakers with Microhpone muted in the Sound Mixer, and when I unmute it, sound comes out (albeit quietly :()).

I would appreciate any help as to why this is happening, and a solution.  Thanks!

---

### Post by LordRaiden on 2006-07-24
Sounds like an alsa bug not a setting issue. I have the alsa-bugtracking link in my signature, so you should report it there.

---

### Post by Turkey Pwner on 2006-07-25
> **LordRaiden said:**
> Sounds like an alsa bug not a setting issue. I have the alsa-bugtracking link in my signature, so you should report it there.
I doubt it's an ALSA bug because it use to work... and I don't think I ever updated ALSA...

[edit]I reinstalled linux-sound-base, alsa-base, and alsa-utils, but that did nothing.
[edit2]I recompiled the ALSA module from source using guide linked to in your signature, but still did nothing.  I guess it is an ALSA bug... but, I don't understand what could be wrong >_<.

---

