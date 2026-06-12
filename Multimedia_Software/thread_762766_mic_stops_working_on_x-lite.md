---
title: "mic stops working on x-lite"
date: 2008-04-22
forum: Multimedia Software
---

### Post by paquinhq on 2008-04-22
Hi everyone this is my first post.

I've installed x-lite on gutsy several times and everything has been working perfectly. I installed it on a PC with a foxconn 865g7mf-sh motherboard. The thing is that this particular cpu has its onboard soundcard broken. I replaced it with an ESS solo-1
ES1938S PCI card since it's a spare that we had in the office and because it's supported by alsa. I disabled the onboard soundcard from bios. X-lite starts with no problems but in the middle of a call (time is variable) I can hear a switch/click on the headset and the microphone dies. But just for x-lite. It works on every other app but x-lite. I`ve tried to run x-lite with oss with no success. What's killing the mic for xlite?  Any help would be appreciated. I ve read that something similar happened with skype. Is there a way to do the same thing on xlite?

Thanks in advance for your help.

---

### Post by mättu on 2008-04-27
I don't know if this helps:
Sometimes my mic switches from "mic1" to "mic2".
Use alsamixer in a terminal to set it back to "mic1".
(use right arrow to "scroll" to mic, then arrow up / down to switch.)

---

