---
title: "Sound &quot;Popping&quot; ?"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Fife3951 on 2009-10-31
Cleanly installed Karmic 9.10 on my HP Pavilion DV2500t.

I get a popping noise each time a sound starts to play, then for the remainder of the sound/song/video/etc, the sound plays fine.  For instance, instead of hearing the chime when receiving an IM, I just hear a "pop."  Same for playing a YouTube video.

I don't know if this helps at all...

```
dan@wehrmacht:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dan@wehrmacht:~$ 

```

Any help would be appreciated.

---

### Post by arst06d on 2009-10-31
I also lost all sound after upgrading, and had to do a fresh reinstall.  Sound now fine except for the "pop", so I'd love some advice too.

---

### Post by mcduck on 2009-10-31
Here's a thread with instructions for disabling powersaving with Intel HDA audio chips See post #5), it should help for popping sound after the soundcard has been idle for a while (and doesn't really have any noticeable effect in battery lifetime anyway):

[http://ubuntuforums.org/showthread.php?t=1289240]("http://ubuntuforums.org/showthread.php?t=1289240")

---

### Post by arst06d on 2009-10-31
top man - seems to have done the trick!

---

### Post by daverich on 2009-10-31
Yup Thanks folks.

(what a poorly implemented feature though,- all they need is a very short fade out/in and it'll fix those clicks)

Kind regards

Dave Rich

---

### Post by []Milo on 2009-11-01
Some very kind and helpful chap uploaded a video describing a process that worked perfectly for me:

[http://www.youtube.com/watch?v=RSbw42MkPvE](http://www.youtube.com/watch?v=RSbw42MkPvE)

---

### Post by Fife3951 on 2009-11-02
> **'[]Milo said:**
> Some very kind and helpful chap uploaded a video describing a process that worked perfectly for me:

[http://www.youtube.com/watch?v=RSbw42MkPvE](http://www.youtube.com/watch?v=RSbw42MkPvE)

Thanks all for the help!  SOLVED!

---

### Post by Zerosoul85 on 2009-11-11
hmm i got the same problem but on windows xp SP3 32 bit... with a x fi titanium AND an asus xonar D1... is there any possibility to change this parameter in win xp ?

---

### Post by vociferous666 on 2009-11-21
ur in a linux forum.  the driver architectures are different between M$ and *nix.  so in short, no, you need to keep on searching the interwebs.

---

### Post by IAmNoodle on 2009-11-22
> **daverich said:**
> Yup Thanks folks.

(what a poorly implemented feature though,- all they need is a very short fade out/in and it'll fix those clicks)

Kind regards

Dave Rich

Would that really work though? The popping is the same as when you boot up any operating system (at least every one I've used), be it Mac, Ubuntu or Windows. I don't know what it is, but something in the computer (probably the sound card. Anyone with any knowledge is free to correct me, for any of this) is transmitting the signal through to the speakers, according to my fading memory of my sound tech course at college. Surely the only way a fade in/out system could be implemented would be within the speakers or with a device in between the speakers and your PC.

---

