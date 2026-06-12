---
title: "Lot of Noise with mics, both internal and external"
date: 2012-03-19
forum: Multimedia Software
---

### Post by dadexix86 on 2012-03-19
Hi! I'm on Ubuntu 11.10, kernel 3.0.0-17.
I've got a big problem with my microphones and sound card
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I experience the problem with both the internal microphone and one part of a headset.

When using them to record sound with Sound Recorder or Cheese or when using them to talk in GTalk or Skype I experience a lot annyoing of noise.

I try to follow some guide on the internet, in fact all are like the answer here: [http://askubuntu.com/questions/8269/microphone-alsa-noise](http://askubuntu.com/questions/8269/microphone-alsa-noise) and it doesn't work.

I tried to troubleshoot following the second guide on the first post here [here](http://ubuntuforums.org/showthread.php?t=1885240) but it says me
```
E: Unable to locate package linux-alsa-driver-modules-3.0.0-17-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-17-generic'
```

Please can anyone help me? What else can I do? What other informations can I provide?

Many thanks

---

### Post by rzippert on 2012-03-19
I'm actually not sure about what can cause it in the software layer, but you can get noise from your electrical installation if it's not properly grounded. I don't think this should be the problem, but it's possible.

---

### Post by coldraven on 2012-03-19
Open a terminal, make it fullscreen and type 
```
alsamixer
```
press F4 to see your input devices, make sure that the mic inputs and mic boost are not too high. You use the L/R arrow keys to select inputs and Up/Down to change the levels.

---

### Post by dadexix86 on 2012-03-19
@coldraven: The Mic Boost is at 30% (below this value no sound is produced) and the Mic volume is at about 60%.

---

