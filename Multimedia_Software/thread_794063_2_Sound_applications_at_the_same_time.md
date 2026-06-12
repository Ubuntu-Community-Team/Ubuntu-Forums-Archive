---
title: "2 Sound applications at the same time"
date: 2008-05-14
forum: Multimedia Software
---

### Post by GuDoN on 2008-05-14
Hello,

I want to know if it is possible to run two media players, or watch flash movies while music is playing, or even play a game while music is playing in the background.

When I do, one application loses sound.

Ubuntu 8.04

Thanks
Graham.

---

### Post by 505 on 2008-05-14
Yes, it should be possible. Look at the program PulseAudio Manager, it should list all the programs that play sound (called clients)

---

### Post by presston on 2008-05-14
1.for multiple sound you must configure asla for your soundcard
2.but flash use OSS. you need to install alsa-oss for it

use search

---

### Post by Vivaldi Gloria on 2008-05-15
> **GuDoN said:**
>  I want to know if it is possible to run two media players, or watch flash movies while music is playing, or even play a game while music is playing in the background.

When I do, one application loses sound.


As far as I understand, if an application uses pulseaudio then it plays nice with other applications. But if an application cannot use pulseaudio then it steals all sound. 

Some apps have settings - if available choose pulseaudio.

For example if i choose alsa in virtualbox it steals all sound but if i choose pulseaudio then things are ok. My favourite audio player MOC does not support pulseaudio so it steals all sound. But i can open several videos in VLC and can hear all. 

Flash problem was discussed in these forums before, search for it. I dont remember if a solution was found.

So play around with settings, try to use apps that can use pulseaudio.

---

### Post by GuDoN on 2008-05-15
I am trying to use Cedega with pulseaudio, but it only supports alsa and oss.

I havent tried the second reply's post yet, but I am sure to when I get home.

Pulse audio fixed my audacity though, never had sound, but now it has!

Does pulseaudio start up everytime I log into my computer? OR is it something I need to open all the time. I installed it from Sypnatic.

---

### Post by Stochastic on 2008-05-15
It should start on boot, but to check simply open gnome system monitor after your next reboot and check to see if PulseAudio is in the list.

---

### Post by ropotamski on 2008-05-15
Chek this
System -> Preferences -> Sound -> Soundtab -> Disable software sound mixing (ESD)

---

