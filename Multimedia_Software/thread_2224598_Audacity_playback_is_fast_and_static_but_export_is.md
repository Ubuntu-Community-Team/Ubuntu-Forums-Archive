---
title: "Audacity playback is fast and static but export is fine"
date: 2014-05-17
forum: Multimedia Software
---

### Post by dannyboy79 on 2014-05-17
I have this really annoying bug with Audacity, i can record my webcam mic using audacity but if i try to playback what I just recorded it plays like twice as fast and it's also all static. I am running Xubuntu 14.04 which has Audacity 2.0.5. A friend of mine has a little work around that appears to work sometimes, it's basically opening pavucontrol, clicking on Configuration tab and for the Built-in Audio I disable it by changing it to off, and then re-enabling it by setting it back to Analog Stereo Duplex and that will sometimes make the file i just recorded playback fine in audacity. Otherwise I dont' get any preview of what I just recorded and I have to blindly export it as a .wav file and when I bring it into kdenlive for my editing it's fine. Does anyone have any clue how to fix this? Would compiling audacity from source fix the issue? My friend says it's a bug with pulseaudio actually not audacity. Can anyone help me?

here's a sample of what audacity does during playback
[https://www.youtube.com/watch?v=nIHKH2i1LM0]("https://www.youtube.com/watch?v=nIHKH2i1LM0")

---

### Post by knight69 on 2015-04-26
I have the same problem with Audacity 2.0.5 on Ubuntu Trusty.  The problem didn't exist until tonight when I was recording music.  Recording is fine and I can export to mp3 with no problems, but I can no longer playback anything.  I can also edit the music (before trying to play it back, but that's difficult when you can't listen to what you are trying to edit.  When I try to play anything (recorded music or imported music) the player appears to go 100x real time and just produces static.  After a moment or two it will freeze and I have to force quit.  I was not able to find the same work around as dannyboy79 found.

---

### Post by Yellow Pasque on 2015-04-28
Try resetting your pulseaudio configuration:
```
rm -r ~/.config/pulse; pulseaudio -k
```

If that doesn't work, I would suspect something's messed up in Audacity's configuration.

---

