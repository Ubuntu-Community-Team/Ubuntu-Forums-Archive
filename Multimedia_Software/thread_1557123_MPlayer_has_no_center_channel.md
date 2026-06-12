---
title: "MPlayer has no center channel"
date: 2010-08-20
forum: Multimedia Software
---

### Post by xluryan on 2010-08-20
I am on amd64, Lucid Lynx (10.04). Using the latest mplayer (MPlayer SVN-r31042-Ubuntu-RVM).

I'm trying to play a hi-def wmv. I get video and audio, but there is definitely some audio missing. The center channel is gone. I have music and sound effects, but the characters dialog is silent.

Any ideas? I know they are in the file because it works fine in Windows (I hate those scenarios :-&).

---

### Post by xluryan on 2010-08-20
Ok, well, I'm not sure why, but switching the audio output driver from alsa to pulseaudio fixed the issue. Weird...

---

