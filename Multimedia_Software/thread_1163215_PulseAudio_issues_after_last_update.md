---
title: "PulseAudio issues after last update"
date: 2009-05-18
forum: Multimedia Software
---

### Post by Kimm on 2009-05-18
Well, the title is pretty self descriptive.

Before the last PulseAudio update (one or two days ago I believe) I started getting issues. Mainly involving Skype. Before, skype worked like a treat with both input and output through Pulse, now all of a sudden it hardly works at all.

When I start skype pulseaudio goes balistic and crashes after a couple of seconds, but then restarts and audio is resumed. I can, for example, call the sound test in Skype, but the sound is incredibly crackly and gives up after a couple of seconds (not to mention: Skype CPU usage goes through the roof).

I've also noticed Pulse crashing when I use Flash and playing movies using mplayer.

I think I might be a problem with the also compatability layer but I cant say for sure. Any ideas?

---

### Post by Kimm on 2009-05-19
Well, this command fixed it:

```
sudo aptitude remove pulseaudio
```

;)

---

### Post by Arup on 2009-05-19
With Skype, its best to select hardware out instead of Pulse, in my system Pulse with skype uses huge amount of CPU sending all my 8 cores into a fit.

---

