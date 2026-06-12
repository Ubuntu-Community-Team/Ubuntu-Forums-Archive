---
title: "No Center Channel in 5.1 sound Karmic Koala"
date: 2010-01-09
forum: Multimedia Software
---

### Post by brian.p.naiman on 2010-01-09
Hi All,

So, I'm working with a relatively fresh install of 9.10, Karmic Koala.  I've got a Sound Blaster Audigy X-Fi sound card and can't get any sound from the center channel in my 5.1 setup.  Iv'e done System->Preferences->Sound->Hardware and chosen "5.1 Analog output + analog mono input" but I get no sound out of my center channel.

Any suggestions?

Thanks.

-Brian

---

### Post by EagleDM on 2010-01-09
Pretty easy.

open a console and type "alsamixer"

move with the cursor to the "center/lfe" channel and press "M" to "unmute"

then use the cursor to up the volume.

Try to put the maximun volume in "master" so you can regulate it with your keyboard or desktop,  remember that Ubuntu rely on PulseAudio and behind Pulseaudio is ALSA  which is the main responsable.


Dunno why it muted by default, but it is.

Also, remember to put the Sound Preferences in 7.1 audio EVEN if you're using 5.1 because otherwise you will get garbled sound and noise in almost every surround application.

Hope this helps.

---

