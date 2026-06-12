---
title: "What are the commands to change the master volume?"
date: 2009-06-22
forum: Multimedia Software
---

### Post by Blue Dolphins on 2009-06-22
Since 9.04 dropped support for my volume control buttons(in addition to other things), and the volume bar panel element is no longer available in 9.04 either, I have to open up the mixer to adjust volume, so I thought I'd assign volume adjusting commands to key combos.  I've tried the following commands, but for whatever reason they don't work.  

amixer set Master playback 1db+ (this command does nothing) 
amixer set Master playback 1db-  (this command sets the volume to 3% instead of decreasing by 1db)  

Am I doing something wrong?  Are there alternative commands that I could try using?

---

### Post by spinoza666 on 2009-06-22
Hey as far as I recall I have used these commands in the past:

amixer set Master Playback 1%+
amixer set Master Playback 1%-

I don't know about decibel, but this will raise your volume by 1%.

Cheers

---

### Post by fillintheblanks on 2009-06-22
works for me..

> amixer sset 'Master',0 playback 5+
amixer sset 'Master',0 playback 5-

---

### Post by Blue Dolphins on 2009-06-22
amixer set Master Playback 1%+
amixer set Master Playback 1%-

These commands work.  I have them set to 5% instead of 1, and they increase by 7% instead, but that's close enough for me.  

Thanks.:)

---

### Post by kerry_s on 2009-06-22
loose the playback & use ticks:
```
amixer set Master 3+ unmute
amixer set Master 3- unmute
```

i do mine by percent, 25,50,75,100 & have it beep to hear it.
sample:
```
#!/bin/sh
amixer set Master 25% unmute >/dev/null 2>&1
aplay $HOME/.sounds/test.wav >/dev/null 2>&1

```

---

### Post by randywolf244 on 2012-02-12
sweet wanted to post on this so can come back to it when im at next to my desktop

---

### Post by andrew.46 on 2012-02-14
In Fluxbox I use the following:

```

# volume settings, using common keycodes
# if these don't work, use xev to find out your real keycodes
123 :Exec amixer sset Master,0 1+
122 :Exec amixer sset Master,0 1-
121 :Exec amixer sset Master,0 toggle

```

The keycodes set the commands to the relevant Fn keys on my laptop...

---

