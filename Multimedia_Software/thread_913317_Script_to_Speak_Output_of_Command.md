---
title: "Script to Speak Output of Command"
date: 2008-09-07
forum: Multimedia Software
---

### Post by i.wanna.corndog on 2008-09-07
Hey all,

I'm trying to set up a script that will get the readout of a command (mpc) and speak *only* the first line of the readout.

Here's the readout of mpc:

```
Def Leppard - Pour Some Sugar On Me
[playing] #12/24   0:00/4:05 (0%)
volume: 20%   repeat: off   random: off

```

I want to just take the title and plug it into espeak like this:

```
espeak "Def Leppard - Pour Some Sugar On Me"
```

I also need the script to pause, then play mpc (since espeak won't work if music is outputting to the sound card).

I can figure out that last part, but I need some help taking the first line of the output and plugging it into espeak.

Thanks!

---

### Post by i.wanna.corndog on 2008-09-07
Well,

I figured it out. This is probably an extremely roundabout way, but it works!

I just have awl remove the second and third lines, then I speak the result.

```
#!/bin/bash
mpc pause
mpc > mpc.txt
awk '{if (NR!=2) {print}}' mpc.txt > mpc2.txt
awk '{if (NR!=2) {print}}' mpc2.txt > mpc3.txt
espeak -f mpc3.txt
mpc play

```

---

