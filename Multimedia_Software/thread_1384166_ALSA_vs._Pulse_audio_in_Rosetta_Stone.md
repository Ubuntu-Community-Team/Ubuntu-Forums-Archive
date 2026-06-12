---
title: "ALSA vs. Pulse audio in Rosetta Stone"
date: 2010-01-18
forum: Multimedia Software
---

### Post by dingo17 on 2010-01-18
I have installed Rosetta Stone but it wouldn't recognise the microphone so I just removed PulseAudio and installed ALSA and it worked just fine but I miss the PulseAudio mostly because it works with Fn-keys on my laptop. 
So I just wanted to ask if there is any way either to make Rosetta Stone work with PulseAudio or to have installed just some parts of ALSA so the mic would work in Rosetta Stone?
I use Wine to run Rosetta Stone.
Thanks in advance.

---

### Post by sports.car.guy on 2010-01-18
Both can coexist together and happily. PulseAudio is a sound client / server environemtn and Alsa on the other hand is more of a hardware abstraction layer meaning it has direct interface with hardware under normal circumstances. 

Install pulseaudio with alsa and everything that would normally run through alsa alone and sent to the sound card is sent from it to pulse instead.

You should be able to have your cake and eat it too with this one.

---

### Post by dingo17 on 2010-01-18
I have installed pulse audio back but now there is no sound at all so I have to killall pulseaudio and force alsa to start. Is there some way to force all programmes to use pulse audio with alsa installed??

---

### Post by Grenage on 2010-01-18
I use Rosetta Stone, but to get the mic working I did have to make same minor changes in the console.  I recall a blog I found that had the answer, will see if I can find it.

---

### Post by dingo17 on 2010-01-18
I've just found this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) , which seems to solve the problem.

---

