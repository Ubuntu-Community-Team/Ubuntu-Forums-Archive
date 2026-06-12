---
title: "RythmBox priority"
date: 2008-11-09
forum: Multimedia Software
---

### Post by LittleKoy on 2008-11-09
I have a quite old pc, so many common operations suck up my CPU for some seconds. During this time, RythmBox stops playing music, obviously because there is no CPU left for it. It can be quite annoying to listen to stop-and-go music every 10 seconds when visiting sites like facebook, or everytime my Dock pops up. This doesn't not happen with Totem of XMMS, for example, but they're not so good at managing music libraries. How can I make that not happen to Rythmbox too?

PS: I have Hardy Heron with RB 0.11.5

---

### Post by bockman on 2008-11-09
I was going to make a similar post, and then I found yours. To ameliorate the problem, you can try to prioritize rhythmbox to -1. 

Type this into a terminal.
```
sudo renice -1 -p `pidof rhythmbox`
sudo renice -1 -p `pidof pulseaudio`
```

Normally, one shouldn't renice less than zero, but there is something wrong with the scheduler in this new kernel. Rhythmbox will freeze occasionally on firefox page loads, big samba transfers, and more. All of this worked perfectly in 8.04, and now is much more laggy. I have a relatively modern computer too (2.5GHz, with 1Gb of RAM). Has anyone else experience this behavior?

---

### Post by LittleKoy on 2008-11-09
That would be the most logical solution, I tried (I set it to -10) but the problem didn't disappear..

---

### Post by bockman on 2008-11-09
Try renicing firefox to +10 or even +15. Today, I am going to recompile this ubuntu kernel and get rid of CFS. I think that this is causing a lot of problems.

---

### Post by LittleKoy on 2008-11-09
When I reboot, will the renicing still be effective or I must do it everytime?

---

### Post by jpeddicord on 2008-11-09
> **LittleKoy said:**
> When I reboot, will the renicing still be effective or I must do it everytime?

Every time; the nice value loses its effect once the process ends. You could make a shell script to launch RB and then renice it. Something like this:

```
#!/bin/sh
rhythmbox &
sudo renice -10 -p `pidof rhythmbox`
```

---

### Post by LittleKoy on 2008-11-09
Thanks.. But if there are more definitive solutions, they're welcome :)

---

