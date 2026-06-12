---
title: "Sound Blaster Live! Value not working in Jaunty (???)"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Pauligrinder on 2009-05-08
Hey,

I recently decided to install Xubuntu 9.04 on my mothers computer because I got fed up with Windows XP. It works perfectly, except for the audio card, a Sound Blaster Live! Value, which has always worked perfectly without having to do anything. Or actually, it appears to be working, because I can get feedback when I turn the volume up with the microphone pointing towards the speakers. The problem seems to be the mixer app (xfce4-mixer). 
It doesn't detect the SB at all, instead it shows some Cirrus-Logic audio card, and changing its settings don't affect sound output at all. Then I tried disabling the SB and going with the integrated audiocard (some intel-thingy)... And guess what: Now it shows the SB, which is disabled, and some other audiocard which I don't have... wtf??? So, I changed the bios settings back to normal, disabling integrated and enabling SB, and now it shows the cirrus-logic again. lspci shows the soundblaster though, which means it is detected (right?). The mixer is also using OSS for some reason, insted of alsa.
I've also tried installing various sound related packages from synaptic, but to no avail. So, what can I do about this??? Thanks in advance.

Oh, another thing. I tried installing gnome-alsamixer. It doesn't show any sliders etc. and when I try to get to soundcard settings, it crashes. I haven't checked terminal output yet, but I will do that asap.

---

