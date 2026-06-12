---
title: "Where is USB? Need specific help."
date: 2007-11-13
forum: Multimedia Production
---

### Post by nicholaspaul on 2007-11-13
I'm trying to get audio setup for recording through an M-Audio Audiophile USB interface (everything goes into a mixer and thru the Audiophile). 

I can get audio playback with Totem. Double click an mp3 and it plays. 

I've tried a few apps, like Rosegarden, Muse, Wired and Ardour and can't get any playback or input. 

Oh yea, and when i'm going through Preferences settings in apps, I don't know where to find the settings to put in there. For example - where do i find the settings for the Audiophile in order to make it the input and output?

Yup, I'm thoroughly confused, and reallyjust need a point in the right direction.
Could someone tell me what info I should post here to begin debugging, because I don't have the faintest idea where to look for audio settings. I have OSS, ALSA, Jack... where do I begin?

---

### Post by Stochastic on 2007-11-14
sounds like all you need to do is start jack on the interface.  open qjackctl and choose your m-audio card, then try to connect.  if all goes well and jack starts then open one of those programs that wern't playing before and try again.

---

