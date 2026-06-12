---
title: "Sound.."
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by Rasymas on 2006-02-18
Greetings people,

Here's what's happening with my system. 

I've tried to configure my sound device by editing some file

```
sudo gedit /etc/esound/esd.conf
```

```
[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2
```

But still I can't play BMP or any other player and watch VLC or other video player with sound at the same time. I have to shut my music player if I want to watch video files.. 

btw.. my Linux DC++ keeps  crashing.. does it has smth to do with the sound?

and 2xbtw.. when I play audio on XMMS or video on VLC some wierd sound plays... like when you turn preamp up to +20db on winamp.. some noisy and totaly dirty sound..

Any soutions...

Thanks in advance

---

### Post by torx on 2006-02-18
software amplifier is pretty bad, so change the volume on your speaker instead of using the preamp. also make sure the PCM settings in the mixer is set at half-way mark, because anything more, software amplifier kicks in and you'll get "noisy and totaly dirty sound".

that's all i can help.

---

### Post by Rasymas on 2006-02-19
I have that one set in the half-way.. but it's still noisy (dirty) dammit, why there'r so many obstacles in ubuntu.. couldn't be there a simple solution for everything... :P

---

### Post by Teroedni on 2006-02-19
First of all
What server do you use in xmms
You need to choice esound server if you wanna share the music with the rest of your system;)

---

### Post by Rasymas on 2006-02-19
Hi,

I used XMMS as the egsample (sp). Anyway.. what should I do if i want to hear music and video file at teh same time? Now I have to shut one of them down in order to hear another..

---

