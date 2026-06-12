---
title: "Nvidia HDMI Audio problem: No system or wine sound"
date: 2009-06-30
forum: Multimedia Software
---

### Post by armitage374 on 2009-06-30
Hi!
Noob here.
I've managed to get most of my sound over on HDMI however my systemsounds and WINE are playing hardball.
 
I'm using ALSA and have made certain that I'm using the ALSA drivers under the WINE configuration, but no go. And even playing the worlds greatest deep space flight sim (Descent: Free Space if anyone is wondering) gets a tad boring without sound.
 
A second, smaller problem is with my system sound. That doesn't play either. 
I've tried the HowTo as well as booting in the older Kernel, nada.
 
I've checked with the sudo alsamixer for muted channels, but all channels seems to be open. 
 
I've even tried with ENVY. 
 
System is as follows:
 
ASUS M3N-H HDMI with Phenom 2 X3 processor
NVIDIA onboard sound/graphics (8200 if I don't misremember)
 
OS:
Ubuntu Jaunty 64 bit 9.04
Driver: Nvidia 180 propritary
Sound system: ALSA
 
As I said, everything else plays fine over the HDMI but system sounds and WINE.

---

### Post by armitage374 on 2009-06-30
WTF?!
 
Out of desperation I just tried out using my headset for playing under wine. I got sound on the headset but still no go on the HDMI.
 
What is wrong with this picture?
 
ETA: It alse seem that I'm getting system sound on  the headset.....Help?

---

### Post by armitage374 on 2009-07-02
Solved it by downgrading to version 173 instead of 180 on the NVIDIA driver. Now I'm just waiting for the bugs to bite me in the rear.....

---

