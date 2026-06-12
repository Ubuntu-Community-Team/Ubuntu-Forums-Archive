---
title: "[SOLVED] No sound when playing divx with Totem"
date: 2008-05-22
forum: Multimedia Software
---

### Post by telemap on 2008-05-22
Hello,

I can play mpg and wmv files with Totem without any problem.

But, when I try to play a divx file with that program, I have the picture but no sound.

Can somebody help me.

Thanks in advance.

Pat.

---

### Post by cor2y on 2008-05-22
Are these recent divx encoded files or older ones from the earlier days of the codec?

---

### Post by wolfen69 on 2008-05-22
do the files play ok with another player such as vlc?

---

### Post by telemap on 2008-05-22
> **wolfen69 said:**
> do the files play ok with another player such as vlc? 
After installing VLC, I had the same problem. I tried to play wmv files but there was no sound at all and it doesn't work anymore with Totem too.

In a thread, I read that installing ffmpeg package can fix the problem. But the result was worst : no sound for all my video files. So I've uninstalled it and after restarting my portable, the problem disappears.

I can now play all my videos with totem and vlc without any problem.

Thanks a lot for your help.

CU.

Pat.

---

### Post by dementic on 2008-11-06
try that : 

terminal and type :

killall pulseaudio

---

### Post by jcsouto on 2008-11-22
> **dementic said:**
> try that : 

terminal and type :

killall pulseaudio

This (very simple command) solved my problem! I had no audio whatsoever in Totem, although I had sound in other applications. Thank you very much

---

