---
title: "Audio and Video problems"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Mr_Knuckles on 2008-09-02
Hello, I'll give my machine's specs first.

Gateway 141-XL Convertable Notebook 

ATI Mobility™ Radeon® HD X2300 256 MB PCI Express graphics
128 MB GDDR3 dedicated memory


The Audio problem: 
This one should be easy. I booted up the other day, and something popped up that I accidentally clicked off of. No clue what it was. Now I have no volume icon in the task bar, and the volume buttons on my keyboard do not work. I think it killed a session script. 


The video problems:
1. How do/ can I make my screen rotate? I read somewhere that this is impossible with ATI video. Is this true? 

2.When playing lots of games, even those that aren't graphics intensive, they flicker horribly. How can I fix that?


Thanks for any help. =)

---

### Post by Mr_Knuckles on 2008-09-02
forgot to mention what I'm running. Ubuntu 8.04

---

### Post by Mr_Knuckles on 2008-09-03
No takers?

---

### Post by Mr_Knuckles on 2008-09-20
help?

---

### Post by stephanvaningen on 2008-10-19
For your second issue: can you tell me if it is still there if you disable compiz?

---

### Post by kingtiger01 on 2008-10-19
for the audio, first thing i would try is to open terminal and use Alsaconfig and see if alsa is working right. if so, right click on youre top menu bar, in a open space and "add to panel" theres a option already there for "Volume Control" i believe this also provides support for the Feature located on youre Keyboard.

Good Luck!

~Kingtiger

---

### Post by stephanvaningen on 2008-10-20
> **stephanvaningen said:**
> For your second issue: can you tell me if it is still there if you disable compiz?
... because if there isn't, then: you can maybe solve it by disabling textured video.
Add the following to your xorg.conf,section "Device":
 ```
Option   "TexturedVideo"   "Off"
```

Source:
 [http://forum.compiz-fusion.org/showthread.php?t=7471](http://forum.compiz-fusion.org/showthread.php?t=7471)

---

