---
title: "vlc mute after seeking forward or backward"
date: 2014-02-26
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2014-02-26
I am experiencing a similar problem as reported here [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/696841](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/696841)
When seeking backward or forward by dragging the progress bar vlc becomes muted. But it my case this only happens with some bluray ripped (hd 720 or 1080p) MKVs,--it doesn't happen for all videos like that, but quite a few. I don't experience this with Smplayer or mpv for the same samples.

Vlc 2.1.3 self compiled on Ubuntu 13.10.

Wonder if this happens in the official build (2.0.8?) or the developmental version (Andrew.46's comments would be greatly appreciated)

Edited: Have tried setting audio output to pulseaudio, automatic and alsa, makes no difference.

---

### Post by andrew.46 on 2014-02-26
> **monkeybrain20122 said:**
> Wonder if this happens in the official build (2.0.8?) or the developmental version (Andrew.46's comments would be greatly appreciated).

I am not much help here as I cannot reproduce the problem which looks like it has popped up in one incarnation or other for several years, going from the bug report :(.  I see a brief but tense exchange in that bug report with Rémi Denis-Courmont which is a little unfortunate as he is one of the vlc developers...

---

### Post by monkeybrain20122 on 2014-03-10
The problem appears to have disappeared after upgrading to vlc 2.1.4.

---

### Post by geoffmen on 2014-12-31
I have this problem, on different computers, and VLC version is 2.1.4. The workaround is to disable and reenable the audio track. no durable solution so far.

---

### Post by syllamo on 2015-07-27
> **geoffmen said:**
> I have this problem, on different computers, and VLC version is 2.1.4. The workaround is to disable and reenable the audio track. no durable solution so far.

I agree - having seen this problem ongoing for a while now, I also go to Audio>Audio Track>disable and then re-enable, this works far better than seeking back and forth in order to get the audio back.

---

