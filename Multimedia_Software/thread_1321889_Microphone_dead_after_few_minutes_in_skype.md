---
title: "Microphone dead after few minutes in skype"
date: 2009-11-10
forum: Multimedia Software
---

### Post by sambarluc on 2009-11-10
Hi,
I have a puzzling problem on my new Ubuntu 9.10 (64bit). Everything works fine, except from microphone. When I start a conversation in skype it works smoothly, but after a few minutes the microphone drops dead, both in skype and outside. If I reboot, it starts working again. Does anybody have the same problem? The problem is exactly the same with other microphones.
Thanks!

---

### Post by shnitz on 2009-11-10
i have quite the same problem !! very frustrating because the mic seems to work OK but suddenly the input stops. i found out that whenever i start firefox the mic stops working.     

i think it has something to do with pulseaudio but it could be an alsa problem also...

i will be VERY grateful if anyone can sort this out !!

---

### Post by shnitz on 2009-11-11
by the way, my system is 9.10 32-bit, bump.

---

### Post by sambarluc on 2009-11-11
I will open a bug on launchpad, please subscribe if you can.

---

### Post by sambarluc on 2009-11-11
Actually there is already one:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/325777](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/325777)

---

### Post by shnitz on 2009-11-12
i think mine is a different bug, sound is still working *fine* and only the microphone is disabled suddenly when i run a certain program (firefox, synaptic etc.).

---

### Post by shnitz on 2009-11-12
any idea on where can i look for a solution to this problem ?
i think its the only thing right now that bothers about the 9.10 and makes me load XP once a day to use skype...

---

### Post by shnitz on 2009-11-13
bump

---

### Post by VertexPusher on 2009-11-13
Have you tried running Skype through ALSA instead of PulseAudio?

---

### Post by shnitz on 2009-11-13
how can i make skype to use alsa and not pulse ?

---

### Post by sambarluc on 2009-11-17
I think you can just change the settings inside skype.

---

### Post by travis_pl on 2010-01-03
I have the same problem on kubuntu 9.10. (skype from medibuntu, alsa). I don't think it has anything to do with firefox - it runs all the time on my computer and my mic works fine, also when I do a Skype testing call, until I make a call that lasts longer (the mic switches off after several minutes). When I reboot it's OK again. 
I've checked all the settings both in kmix and alsamixer - seem to be OK... 
Any suggestions?

---

### Post by jperelli on 2010-07-13
I have exactly the same problem.

It works great, but about 4 minutes later, the mic just doesn't work anymore.
If i close an open again skype it works for another 3~4 minutes.

Nobody solved this??

---

### Post by lidex on 2010-07-14
Uncheck the option in skype to change mixer levels.

---

### Post by sambarluc on 2010-07-22
Just dig into the preferences menu of skype.

---

