---
title: "[SOLVED] Hardy Sound Issues"
date: 2008-07-24
forum: Multimedia Software
---

### Post by tankfists on 2008-07-24
I'm having a problem with my audio. It works when it wants to, basically. I followed advice from this post ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) and managed to fix flash a bit. By that I mean, audio might cut off at any moment, but I can refresh the page and it will work again. For a while.

On the other hand, rhythmbox, exaile, and banshee all cut off the audio under one minute into playing a song. Exiting the music player and then starting it again works, but its frustrating. There's no error message that occurs when the audio cuts off. In vlc the song simply keeps playing, while in other music players the song stops. Skype calls also don't work, displaying an error message when a call is attempted.

I'm not sure what happened that broke the audio, except that it was a recent update (maybe within the past two weeks). Following advice from the sticky, I've tried setting the system default to pulse audio, and then to alsa, but neither fixed my problem.

If it matters, my computer is a toshiba satellite A75.

---

### Post by tankfists on 2008-07-26
Doing a complete re-install didn't work. Strange. My audio was working before, on an laptop I upgraded through the previous two versions.

Edit: Re-installing gutsy didn't work either.

---

### Post by Yellow Pasque on 2008-07-26
Try OSS4 (link in sig).

---

### Post by tankfists on 2008-07-30
Installing OSS4 worked. Thanks.

---

