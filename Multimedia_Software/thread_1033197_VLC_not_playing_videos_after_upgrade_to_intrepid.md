---
title: "VLC not playing videos after upgrade to intrepid"
date: 2009-01-07
forum: Multimedia Software
---

### Post by anilcr on 2009-01-07
Hi guys I upgraded to intrepid ( amd64 ) from hardy ( amd64 ) yesterday but now vlc doesn't play any videos but i can hear the sound but it won't play the video :(
I run a amd64 with a nvidia graphics card

---

### Post by anilcr on 2009-01-07
OK this is also happening on ubuntu :(

---

### Post by anilcr on 2009-01-07
pop

---

### Post by anilcr on 2009-01-07
:confused: help :confused:
somebody? 
anybody?

---

### Post by rossmoore on 2009-01-07
If it helps, I'm getting the same behaviour in Ubuntu. But only on some videos. Some of my vobs don't play at all, but if I use mplayer or mencoder to rebuild the index then vlc is able to play the audio but not the video. Mplayer is able to play the same file.

All very peculiar - and VLC in Hardy was able to play these videos. It's like VLC is being more picky than it used to be, and that it thinks something is not quite right with them.

---

### Post by anilcr on 2009-01-07
well, mplayer and totem play all vids, and i do have all the codecs i need this is the error it throws:
[B][00000001] main libvlc debug: translation test: code is "C"
[00000500] main video output error: no video filter module matched "adjust"
[00000500] main video output error: no suitable vout module
[00000466] main decoder error: failed to create video output
mdb:134, lastbuf:0 skipping granule 0
[00000502] main video output error: no video filter module matched "adjust"
[00000502] main video output error: no suitable vout module
[00000466] main decoder error: failed to create video output[/B]

so I think this is a problem with vlc...

---

### Post by anilcr on 2009-01-07
try this :
tools->preferences->reset
worked for me!
gud luck

---

### Post by sayakb on 2009-01-07
Switch to X11 output mode. VLC -> Tools -> Preferences -> Video and choose "X11 output module" from the Output drop menu.

---

### Post by rossmoore on 2009-01-08
The problem isn't that VLC isn't displaying video output per se. The problem is that VLC displays video output for DVDs and most video files, but for some video files it fails to display video, only playing the audio.

In Hardy the video file that misbehaves played fine with VLC, and in Intrepid the video file that misbehaves plays fine with mplayer; the misbehaving video just doesn't play with VLC in Intrepid, despite the fact the VLC in Intrepid can play most other videos very successfully.

---

