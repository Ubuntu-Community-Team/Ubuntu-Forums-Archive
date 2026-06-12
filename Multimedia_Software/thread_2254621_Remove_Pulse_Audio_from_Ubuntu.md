---
title: "Remove Pulse Audio from Ubuntu?"
date: 2014-11-28
forum: Multimedia Software
---

### Post by i12 on 2014-11-28
I wanna remove pulse audio from my 14.10 but I afraid to dertroy all sound output.
There is the post on our loved forum[http://ubuntuforums.org/showthread.php?t=2226316&highlight=remove+pulse+audio](http://ubuntuforums.org/showthread.php?t=2226316&highlight=remove+pulse+audio) buts  2 years old.

---

### Post by Rob Sayer on 2014-11-29
Removing pulseaudio is not a good idea.  It has a shedload of dependencies and you'd likely end up regretting it.

Why do you want to remove it?  What's the actual audio problem?

---

### Post by Yellow Pasque on 2014-11-30
It's a bad idea, especially if using Gnome or Unity.

---

### Post by i12 on 2014-12-01
> **Rob Sayer said:**
> 
Why do you want to remove it?  What's the actual audio problem?



But it slows real time sound soft sythesizers. I cant play music. part of second reply makes it impossible.

---

### Post by Rob Sayer on 2014-12-03
> **i12 said:**
> But it slows real time sound soft sythesizers. I cant play music. part of second reply makes it impossible.

Maybe it's a language problem but that doesn't make much sense.  What are "real time sound soft sythesizers"?  What software are you usiing anyway?  What output modules in those programs are you using?  Try setting them to ALSA.

---

### Post by i12 on 2014-12-10
Bristol, Zynaddsubfx. Previous years, good sence for composer was to remove pulse audio after installing Linux

---

### Post by Rob Sayer on 2014-12-10
> **i12 said:**
> Bristol, Zynaddsubfx. Previous years, good sence for composer was to remove pulse audio after installing Linux

100% wrong ...

Never uninstall pulse.  Just disable it if pulseaudio actually is the problem.

---

### Post by mörgæs on 2014-12-10
If you don't like Pulseaudio it's better to begin with a fresh install of Lubuntu which does not have Pulseaudio by default.

---

### Post by Rob Sayer on 2014-12-10
> **mörgæs said:**
> If you don't like Pulseaudio it's better to begin with a fresh install of Lubuntu which does not have Pulseaudio by default.

That's quite possibly a good idea ... Lubuntu uses alsamixer instead, and it may be easier to do it this way.

---

### Post by i12 on 2014-12-10
I launched bristol with alsa but it is very low volume. I've launched zynaddsubfx with alsa. The same low volume. Interesting thing is pulse audio not guilty in big latency the guilty is jack. With alsa zynaddsubfx is very quick I cant fill any delay. Lets think thread is closed thanks to everyone involved.

---

