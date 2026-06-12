---
title: "Other Sounds does not play after zynaddsubfx is started."
date: 2013-08-23
forum: Multimedia Software
---

### Post by hariks0 on 2013-08-23
I have installed and running zynaddsubfx. However I find a particular problem with it. Once I start zynaddsubfx, no other sounds work in my PC. It is so even if I quit zynaddsubfx. I have tried logoff and login but to no avail. The only way I can restore the sound is by restarting the PC. Initially, I was not able to use zynaddsubfx as there was no audio output from it. However, I installed QJackCtl and edited the shortcut of zynaddsubfx as follows:
```
zynaddsubfx -I alsa -O jack -a
```

Now, I get the audio output from zynaddsubfx, but only from zynaddsubfx, nothing else. Again, restarting the PC restores the normal audio like Media player, streams etc.

Please help me to switch between the Audio outputs or better have all other normal audio and zynaddsubfx simultaneously.

TIA.):P

---

### Post by hariks0 on 2013-08-25
Bump ! No takers, yet?

---

### Post by carmariosonic on 2014-07-29
You're going to want to type

[COLOR=#000000]Code:[/COLOR]
sudo alsa force-reload

[COLOR=#000000][/COLOR]For me, this terminates the program's hold on my sound card, but it gives me a weird buzzing sound. If this happens to you, just hit the command one more time, and you should be golden!

---

### Post by QIII on 2014-07-29
This thread is nearly a year old.

Closed.

---

