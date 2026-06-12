---
title: "MPlayer and VLC start all video overlays with Black Screen of Death"
date: 2010-07-10
forum: Multimedia Software
---

### Post by sorabsuperstar on 2010-07-10
MPlayer and VLC start all video playback with a Black Screen of Death, lasting for ca 3 to 5 second. Though afterwards the screen comes back and video plays without problems (in a window), this is pretty(!) annoying.
When exiting Mplayer, the BOD comes up again (but this one only happens with MPlayer, NOT with VLC)

The phenomenon does only occur with video files, not with audio files. It does not at all occur with Xine based players (Kaffeine, Dragon).

I tried XV and OpenGL as output, same problem with both.

System: 
Kubuntu Lucid AMD64 on Phenom II x4; 
Catalyst 10.4 (aka 8.72.3) video driver on a Readeon HD 5770

Any ideas?

---

### Post by t0rb3n on 2010-07-12
I've a similar issue, although in my case, the video never start showing up with either mplayer and vlc ... there is a blink of the images if i switch to fullscreen and back, but then it just stays black. sound is played just fine...

i'm on lynx 32bit @ amd64 3800+, catalyst 10.4 @ HD4770

---

### Post by lucaspl81 on 2010-07-12
Setting vo to gl2 resolved this for me, although I still get some jagging when playing video with quick animation without nvdpau (2560x1440 via Display Port).

---

### Post by t0rb3n on 2010-07-15
> **lucaspl81 said:**
> Setting vo to gl2 

can you explain, please?

---

### Post by t0rb3n on 2010-07-26
okay, figured something out... 

first, vlc played if i did not move the mouse in fullscreen.
then i saw fglrx giving errors like 

```
(WW) fglrx(0): Cannot get updated TV attributes.
(EE) fglrx(0): Failed to allocate dynamic shared buffer!
```

i dont know what to make of them...

anyway, i set my visual effect to none, and now video works fine...

---

