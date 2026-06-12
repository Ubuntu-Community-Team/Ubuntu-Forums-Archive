---
title: "Audio Output problem"
date: 2010-04-11
forum: Multimedia Software
---

### Post by fabiotheimpaler on 2010-04-11
I'm having a bit of a problem with my sound output. I'm running Ubuntu 9.10.  Whenever I try to use my monitors for sound output, I get what sounds like a clip every two seconds or so.  When I try to run JACK, I get an Xrun every time the sound clips.  It started doing this after I installed the latest kernel update.  Any ideas?

---

### Post by cchhrriiss121212 on 2010-04-14
Xruns are the sound distortion, as it is a notification that jack cannot process what you are doing fast enough. From the sounds of it, you have upgraded from a real time kernel to a generic one, so switch back to the rt in grub.

---

### Post by fabiotheimpaler on 2010-04-14
I tried it.  The sound is STILL glitchy and jumps even on the RT Kernel.  I tried setting up a .asoundrc file, like some of the other audio problem threads suggested, but it still doesn't work properly.  I've also clean installed twice, no solution.

---

### Post by cchhrriiss121212 on 2010-04-14
This is a jackd problem so you don't need to use an .asoundrc file. Xruns are also caused by settings that are too high. Could you post your jack settings window, or the output of ~/.jackdrc?

---

