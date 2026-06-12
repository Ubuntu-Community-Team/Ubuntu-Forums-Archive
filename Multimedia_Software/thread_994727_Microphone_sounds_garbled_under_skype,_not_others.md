---
title: "Microphone sounds garbled under skype, not others"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Xorlium on 2008-11-27
Hi everyone,

I have a laptop, asus G50Vt, and I connected a mini microphone (creative) to it. If I go to skype (which I installed from medibuntu), when I try to speak it sounds garbled and with a looot of static (it's not understandable, but it's clearly picking up my signal). I've tried playing around in alsamixer (and kdemix) but nothing.

Oh, and recording in audacity, for example, works perfectly with pretty good sound quality. It's only in skype it doesn't work.

Thanks!
Xorlium

(Oh, I forgot to mention: I'm using kubuntu 8.10, everything up to date. The sound system is intel ICH 9)

---

### Post by Stochastic on 2008-11-27
I ran into this problem on 8.10 as well; I found that if you go into skype's options (ctrl+o) and select the sound devices section, there you can set skype to use your hardware directly and this gets rid of the garbled-ness.  I think this stems from skype not properly implementing pulse audio, but I'm not sure (skype is closed source, so we may never know).

---

### Post by Xorlium on 2008-11-27
Strange, I tried that, and changed both sound in and sound out to everything possible, and not one of the 6 options I had works. I mean, it doesn't sound garbled anymore... it doesn't sound at all.

If I try to make a "skype test call" it says there was a problem with my audio recording settings.

Thanks!
Xorlium

---

