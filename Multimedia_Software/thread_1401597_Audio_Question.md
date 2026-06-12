---
title: "Audio Question"
date: 2010-02-08
forum: Multimedia Software
---

### Post by bullu on 2010-02-08
I was wondering if there is any default equalizers for my audio device in Ubuntu.
Coz i my sound while playing videos/audio from live streaming sites are quite bad. But while playing frm my hard drives using VLC i can equalize to make it better so i was wondering if there was a way to equalize my default sound...
Also when I look into the sound prefrences it only shows INTERNAL AUDIO but not my actual sound card..
Ubuntu 9.10 Karmic

---

### Post by mörgæs on 2010-02-09
This discussion is a little old, but maybe you can find some ideas:
[http://ubuntuforums.org/showthread.php?t=328620](http://ubuntuforums.org/showthread.php?t=328620)

---

### Post by Enigmapond on 2010-02-09
To date, there is no system-wide EQ available only programme specific as in VLC or Banshee and the like which have their own EQ's...I don't think the devs think this is important enough to work on unfortunately...

---

### Post by johoe on 2010-02-09
Thats not quite correct - have a look at this:
[http://ubuntuforums.org/showthread.php?t=1308838]("http://ubuntuforums.org/showthread.php?t=1308838")

and this:
[http://ubuntuforums.org/showthread.php?t=1378087]("http://ubuntuforums.org/showthread.php?t=1378087")

johoe

---

### Post by VertexPusher on 2010-02-09
> **Enigmapond said:**
> To date, there is no system-wide EQ available only programme specific as in VLC or Banshee and the like which have their own EQ's...I don't think the devs think this is important enough to work on unfortunately...
System-wide EQs exist for both ALSA and PulseAudio, but they are not included in the default repositories for good reasons. Most digital audio streams are normalized or compressed to use the entire dynamic range, i.e. there is no headroom left. If you use a system-wide equalizer in the digital domain to boost treble or bass of such a stream, you'll make the audio signal hit 0 dBFS and get clipped. Clipping is bad because it can damage your amplifier or speakers.

[http://en.wikipedia.org/wiki/Clipping_(audio)](http://en.wikipedia.org/wiki/Clipping_(audio))

---

### Post by bullu on 2010-02-09
Thanks guys,
I installed the PulseAudio equalizer and it seem to work now the sound is better..
But still my Ubuntu shows INTERNAL AUDIO rather then the actual Audio device..

---

