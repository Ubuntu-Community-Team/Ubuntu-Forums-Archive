---
title: "sound not working"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by jnev on 2007-09-05
I just reinstalled ubuntu on my desktop, and the sound isn't working. all of volume controls are turned on. I've been using ubuntu for close to two years now, and this is the first time that it hasn't been automatically detected and working. I've even installed feisty before from this same CD and it has worked...

anyways, I'm really not sure what to do to fix it. when I go to system -> preferences -> sound it shows that my sound card (creative audigy ES) is autodetected (as is the onboard sound from my mobo, but sound doesn't work out of there either, I checked). sound playback under sound events, music and movies, and audio conferencing is all set to autodetect, and changing from autodetect to any of the other choices doesn't do anything. sound capture under audio conferencing is set to alsa. 

help would be much-appreciated.
thanks

---

### Post by jnev on 2007-09-06
bump... can someone help me?

---

### Post by trellis2 on 2007-09-06
Is ESD one of your options? Of course U have already checked the usual suspects: mute, PCM. etc in Volume control. Try “killall esd“ from a terminal window and restart if ESD is one of the sound playback options.

---

