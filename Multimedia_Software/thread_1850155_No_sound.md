---
title: "No sound"
date: 2011-09-25
forum: Multimedia Software
---

### Post by kens60 on 2011-09-25
Just got in today and I have no sound at all... I do on windows, but nothing at all in ubuntu.

---

### Post by jackluu on 2011-09-26
have you checked whether mute is on? click on the sound icon in the panel.

---

### Post by kens60 on 2011-09-26
Yes,

---

### Post by ciscoboy on 2011-09-26
I have a similar problem; My sound applet is set on mute, and it says "mute all" in a way where it's locked (so I can't change it), and there's no way that I can increase the volume except on whatever I'm using (i.e.: youtube, internet video, video player...). But the thing is, the volume is set low; i can still hear what someone is saying if someone's talking.
I also tried to access the sound preferences (from the upper bar and from the preferences menu), without success.

Any advice?

Ciscoboy

---

### Post by kens60 on 2011-09-26
I don't get any sound at all and all of my settings are NOT muted.... I am thinking my sound card is only for WINDOWS   It is a Xtreme Sound PCI card.

---

### Post by .... on 2011-09-26
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by kens60 on 2011-09-26
RECEIVED THIS ....

Could not open location 'file:///home/kens60/cd%20~/%0A%20%20wget%20http:/www.alsa-project.org/alsa-info.sh%20-O%20alsa-info.sh%20&amp;&amp;%20bash%20alsa-info.sh'

---

### Post by Toz on 2011-09-26
From a terminal window:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```, choose upload option and post back link.

---

### Post by kens60 on 2011-09-26
Solved the No Sound problem.......

I went into BOIS and SOUND was marked ON, turned it to OFF ........  I found this advice on GOOGLE, this guy said," Make your life easy, simply disable the on-board audio in the BIOS setting of your motherboard, that the two were not compatible. So I'm now only using the sound card I installed, Xtreme Sound PCI card...because it is not compatible with the original motherboard sound.   AMAZING.....

Thanks for the help guys...

---

