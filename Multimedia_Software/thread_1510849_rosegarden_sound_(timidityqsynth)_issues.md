---
title: "rosegarden sound (timidity/qsynth) issues"
date: 2010-06-16
forum: Multimedia Software
---

### Post by ivankaramazov on 2010-06-16
hey guys,
i've been working on trying to get timidity/qsynth to work with anything. i installed freepats, downloaded some sf2 files and nothing seems to work. actually, i occasionally get sound from timidity after i close rosegarden but that's about it. qsynth either crashes or does nothing at all.

i did get sound in rosegarden using zynaddsubfx and amsynth. my other apps (lmms, the 2 synth i mentioned, audacity, hydrogen) work better in the alsa settings then they do in jackd -- i guess what i'm saying is, how do you get a general midi softsynth (be it qsynth/timidity) to work, and hopefully without jackd?

im tempted to format everything and install ubuntu studio, but guitar pro 6 only allows 5 installs, and i kinda need that program for work.

mike.
ps, im running 10.04 on a compaq presario c700 dual core 1.6 ghz with 1 gig ram

---

### Post by cchhrriiss121212 on 2010-06-16
Any reason you are not wanting to use jack? If you install a real time kernel you will basically have everything studio has, in addition to improved performance over the generic kernel.

---

### Post by ivankaramazov on 2010-06-16
i'm running kernel 2.6.32-22 generic. i downloaded the linux-rt package which did nothing. i tweaked the limits.conf to allow realtime computing. 

jack is very unreliable on my system. when i do get it to behave, alsa sounds way better. actually, alsa sounds pretty darn good. so back to getting timidity or qsynth to work, unless someone knows of any other good programs.

edit: chris, i noticed that your running karmic. maybe they're still working on getting all the bugs out of lucid. i don't know if its even 2 months old yet.

---

### Post by cchhrriiss121212 on 2010-06-17
Jack has the same sound quality as ALSA, as jack is just a frontend for ALSA. What jack offers is not an improved sound, but improved latency and functionality which is very useful when using multiple programs as you are.
When you download a new kernel you have to boot into it at GRUB, you can use startup manager to select default kernels, which you can download from synaptic.

Qsynth is a GUI for fluidsynth, so check you have that installed. When you open up qsynth, you need to load a soundfont and then connect an instrument or sequencer to it.

---

### Post by ivankaramazov on 2010-06-18
wonderful.

i needed a pack like startup manager to switch back and forth between kernels. thank you so much, i would have never thought to look for it myself.
 
realtime works, timidity works, i can use the general midi sounds in rosegarden (both freepats and the r3 sound font). jack will work in due time, its a matter of setting it up. so, yeah ... thank you kindly.

---

