---
title: "Need help with recording my desktop?"
date: 2012-05-03
forum: Multimedia Software
---

### Post by Rush The Hedgehog on 2012-05-03
Hey there I want to record my desktop using the program recordmydesktop, but how do I get sound for it?
I'm using Ubuntu 12.04. Please help.

---

### Post by Rush The Hedgehog on 2012-05-03
I've found out how to do it, but whenever I record the sound sound's horrible, how do I fix that.

---

### Post by SysBoot on 2012-05-03
Try recording the sound with audacity and the actual screen with recordmydesktop then slap them together.
```
 sudo apt-get install audacity
```

---

### Post by Bonster on 2012-05-03
install *pavucontrol*

then change the pulseaudio sound as you like

---

### Post by Rush The Hedgehog on 2012-05-03
I have all of that, why is my sound acting so weird, it goes all horrible on me?

---

### Post by shantiq on 2012-05-03
> **Rush The Hedgehog said:**
> Hey there I want to record my desktop using the program recordmydesktop, but how do I get sound for it?
I'm using Ubuntu 12.04. Please help.



got a little **[howto]("http://ubuntuforums.org/showthread.php?t=1710642")** here for this purpose


for just sound **[this]("http://ubuntuforums.org/showpost.php?p=11053351&postcount=9")**

---

### Post by Rush The Hedgehog on 2012-05-18
Can I upload an example video here of what noise I get?

---

### Post by Rush The Hedgehog on 2012-05-18
This is the noise I get consistently :(. 

**[http://www.mediafire.com/?5bj1igl57k5m0uj](http://www.mediafire.com/?5bj1igl57k5m0uj)**

If you can hear a screeching noise like a Banshee that's what noise I get after recording.

---

### Post by enigma32 on 2012-05-18
I'd wager a guess that this is digital feedback. You might want to take a look through your audio mixer (I usually use alsamixer, but gnome has a GUI too) and make sure you don't have an output routed into your input somewhere.

---

### Post by Rush The Hedgehog on 2012-05-18
Well I use a Microsoft web cam so I was also wondering if that could be a problem too? I also use kazam screen caster, and I saw a guy on you-tube using it and it seemed to work fine for him.

---

### Post by Rush The Hedgehog on 2012-05-18
Really would like some professional help on this ;).

---

