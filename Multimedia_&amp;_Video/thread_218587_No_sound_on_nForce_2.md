---
title: "No sound on nForce 2"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by Jalexxi on 2006-07-18
Okay, I've tried everything I could find on these forums and on Google, and so far nothing has worked. As I understand it, the nForce 2 drivers should be built into Ubuntu. I've tried installing the nForce drivers from the Nvidia site, but it wants me to compile my own drivers, for which I need C libraries, which is all complicated, and too much for my poor head which has been attempting to understand Linux for two days now after over ten years of using Windows. And it should work with these drivers, anyway. I've followed the Sound guide here, did things like unmute everything in alsamixer, unmute everything but the External Amplifier, but nothing seems to work. Now I'm just getting frustrated, and I'm in need of suggestions!

---

### Post by croak77 on 2006-07-18
When you run alsamixer, what does it say at the top after Card or Chip? I have a nforce2 board. It uses the snd_intel8x0 module. Open a terminal and type 'lsmod'. Look for snd_intel8x0 if it's not there type 'sudo modprobe snd_intel8x0.

---

### Post by Jalexxi on 2006-07-18
Already did so, even set it up to load the intel8x0 driver at startup. No sound, though. In regards to cards and chips, alsamixer gives the following:
Card: NVidia nForce2
Chip: Realtek ALC650F

---

### Post by Jalexxi on 2006-07-19
A little added note that might be of interest (I'm not sure)... When I run alsamixer just by typing 'alsamixer', it says 'no mixer elems found'. So instead I run alsamixer using 'alsamixer -c 0'. Maybe that's significant in any way?

---

