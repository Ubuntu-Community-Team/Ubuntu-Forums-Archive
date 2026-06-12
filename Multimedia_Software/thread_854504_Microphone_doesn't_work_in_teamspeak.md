---
title: "Microphone doesn't work in teamspeak"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Nightbox on 2008-07-09
Hello, 

I have installed teamspeak 2.0.32.60, however the microphone doesn't work. I can hear myself in the speakers when I talk, also, I can record using gnome 'sound recorder', so I guess my microphone is ok. Furthermore, I searched on google and found a little test to see if /dev/dsp is working:
```

cat /dev/urandom /dev/dsp

```
after running the command, I can hear a rumbling noise in my speaker.
any help would be apreciated.

---

### Post by ex.hav0k on 2008-07-29
try using /dev/dsp1 as the sound driver under teamspeak's options

---

