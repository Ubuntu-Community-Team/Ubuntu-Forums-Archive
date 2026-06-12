---
title: "distorted sound with SB Audigy LS"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by hellblade on 2007-10-22
Hi. I have a Sound Blaster Audigy LS and while everything seems to work fine, when the volume (kmix) is set to more than 80%, the output gets distorted. The higher the volume, the worse it gets.

Now my question is where should I report this bug? Alsa? Kernel driver maintainer?
Anyone else has this problem?

```

$ lspci -v | grep audio
04:07.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

The driver for this card is CA0106.

---

### Post by toydoctorrrs on 2007-12-15
bump, 
same problem, same card.
running Gutsy 
card: 04:04.0 Multimedia audio controller: Creative Labs SB Audigy LS

---

### Post by toydoctorrrs on 2008-01-13
I did a Kernel recompile 2.6.23.13 without oss and alsa as module, the distortion over 70% sound is fixed, but sometimes there is crackling and firefox crashes while playing flash.

someone?

---

### Post by forezt on 2008-05-30
I had distorted sound on this card as well.

First, make sure that your speakers are plugged into the green jack (analog out) and not the blue (digital out). 

Then, go into alsamixer (type "alsamixer" into a terminal) and mute the digital output (IEC958) by highlighting "IEC958" and pressing "m".

---

### Post by toydoctorrrs on 2008-06-01
It works now on 8.04 with PulseAudio I suppose.
tried it and crispy loud sound came out of the speakers

---

