---
title: "sound device changes to dummy output"
date: 2010-03-27
forum: Multimedia Software
---

### Post by joshwaaa on 2010-03-27
Hi All,
 
I finally got audio working on my ubuntu 9.10 desktop... now I am having sound issues watching movies from a network share.

The sound device continually randomly changes to "dummy output device" and then there is no sound output. The sound icon dissapears on the toolbar. To get it back and audio to start working I have to sudo alsa force-reload.

It seems to happen everytime there is a network delay, the movie will stop for a second and then when it plays the sound is gone. 
 
Is pulse locking out the audio or something? Do I need to somehow enable multi apps to use sound?

any ideas?

Cheers,

**[COLOR=#ff0000]Joshwaaa[/COLOR]**

---

### Post by maximus2010 on 2010-03-27
Its a hardware problem , your sound card is crashing.

---

### Post by spooled_u on 2010-03-27
> **joshwaaa said:**
> Hi All,
 
I finally got audio working on my ubuntu 9.10 desktop... now I am having sound issues watching movies from a network share.

The sound device continually randomly changes to "dummy output device" and then there is no sound output. The sound icon dissapears on the toolbar. To get it back and audio to start working I have to sudo alsa force-reload.

It seems to happen everytime there is a network delay, the movie will stop for a second and then when it plays the sound is gone. 
 
Is pulse locking out the audio or something? Do I need to somehow enable multi apps to use sound?

any ideas?

Cheers,

**[COLOR=#ff0000]Joshwaaa[/COLOR]**


What were your initial issues and how did you over come them ? I'm getting intermittant sound in 9.10 64 bit.. I can hear youtube and flash sound, but mplayer or anything local doesn't play... 

What soundcard are you using ?

---

