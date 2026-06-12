---
title: "Sound is working but sounds odd"
date: 2011-07-04
forum: Multimedia Software
---

### Post by selenir on 2011-07-04
My sound is working, though the problem is a bit difficult to describe. The sound seems to be off, not playing certain particular frequencies. I have gotten the sound to work on Windows, so I do not believe it is a hardware problem.

I do not understand the KDE sound system well enough to know where to start. I have tried removing PulseAudio to use ALSA, but the problem still seems to be there. I believe I picked the correct driver for ALSA, also with no effect. I tried Xine instead of GStreamer, but that also did not help. Any advice would be appreciated.

---

### Post by selenir on 2011-07-05
I have discovered that people often have problems with the snd-hda-intel module for ALSA. I have tried picking my model, but that has not helped. From what I understand, programs in KDE use Phonon, which relies on a backend, which in turn relies on ALSA. Someone correct me if I am wrong.

---

### Post by lidex on 2011-07-06
Always start with the basics. Try adjusting your surround/side/lfe levels in alsamixer.

---

### Post by selenir on 2011-07-06
All of them are maxed and unmuted. 

EDIT: I am confounded. Sound is now working perfectly. Why are my problems fixing themselves? It may have been because I used Alsamixer. I'll restart and give it another try.

EDIT 2: I've rebooted a couple times, and it seems that Kmix keeps muting my sound on login. Otherwise, my sound is fine. It's less annoying than having wonky sounds, but it would be nice if I could get that fixed. I wanted to reinstall Kubuntu because of various muck-ups I've done but I'm terrified of having to go through the same process.

---

### Post by lidex on 2011-07-06
> **selenir said:**
> All of them are maxed and unmuted. 

EDIT: I am confounded. Sound is now working perfectly. Why are my problems fixing themselves? It may have been because I used Alsamixer. I'll restart and give it another try.

EDIT 2: I've rebooted a couple times, and it seems that Kmix keeps muting my sound on login. Otherwise, my sound is fine. It's less annoying than having wonky sounds, but it would be nice if I could get that fixed. I wanted to reinstall Kubuntu because of various muck-ups I've done but I'm terrified of having to go through the same process.

Have you checked kmix configuration:
[http://ubuntuforums.org/showpost.php?p=623917&postcount=6](http://ubuntuforums.org/showpost.php?p=623917&postcount=6)

---

### Post by selenir on 2011-07-06
That fixes the Kmix problem for me but the distorted sound problem is back. Something seems to go wrong when I open up Phonon. 

EDIT: It also seems to have something to do with PulseAudio. When I killed it, the sound quality was restored.

EDIT 2: PulseAudio or anything using it. When I killed it, it restarted and then sound quality was restored.

---

### Post by lidex on 2011-07-06
Try resetting your  pulse configuration:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 

```
**Logout/in.**

---

### Post by selenir on 2011-07-10
My sound problems seem to be fixed. Thanks a lot.

---

### Post by lidex on 2011-07-10
You're welcome. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by selenir on 2011-07-19
The problem has showed up again. Any of the previous solutions do not seem to resolve the problem. I may be a hardware problem as I just installed a video card, although the problem was present before, when I made the thread.

---

