---
title: "No sound on tuxguitar, all other programs have working sound"
date: 2012-08-02
forum: Multimedia Software
---

### Post by kerryhall on 2012-08-02
Just wanted to note (possibly file a bug report if needed) that after a fresh install of 12.04, doing an apt-get install tuxguitar, there is no sound output in tuxguitar. Sounds works in all other applications.

FIX:
I fixed this by doing an apt-get install timidity, then selecting timidity in the drop down selection for midi port in tux guitar. Perhaps this should be the default? (ie, installing tux guitar should also install timidity + change that drop down selector box) Any other ideas?

Should/how do I file a bug report for this?

---

### Post by FBMinis on 2012-08-10
Let me take the liberty to use your topic, as I'm having the same trouble.

Installed Tuxguitar, tuxguitar jsa and Timidity. However, it did not change the drop down menu.

Bowsed Tuxguitar forum and found the following topic:

[http://tuxguitar.herac.com.ar/forum/5/1917/no-sound-in-tuxguitar/](http://tuxguitar.herac.com.ar/forum/5/1917/no-sound-in-tuxguitar/)

Taking their advice and RUNning:

timidity -iA -A170 -B3,10 -Os -EFreverb=0 2>&1 >/dev/null&

This changes the dropdown menu and gives me the option TIMIDITY  PORT 0 (and others), which makes the program work, there is sound indeed.

However, when I restart my computer, I have to RUN that code line again...

How can I fix this?

Thank you.

---

### Post by FBMinis on 2012-08-13
Ok, it's working for me after I did it this way:

1. Open Synaptic
2. Install Timidity and Timidity Daemon
3. Install Tuxguitar (did not install **tuxguitar jsa**)

F

---

