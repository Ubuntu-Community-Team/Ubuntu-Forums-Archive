---
title: "sound input on Audigy LS"
date: 2006-01-14
forum: Multimedia &amp; Video
---

### Post by sparky on 2006-01-14
Hi,
Apologies if this has already been answered, but I did a search and did not get anything definite.  I have breezy installed on my computer AMD 2000, 256 mb ram, sound blaster audigy ls.  Playback of sound works just fine, but sound input via microphone or line in seems to be dead.  And yes to answer the obvious, I did make sure these devices were unmuted.  Any help or suggestions would be appreciated, because I would like to use my linux box to run some amateur radio software, which requires sound input.  Thanks in advance.

Peace,
Sparky

---

### Post by Mr_Grieves on 2006-01-14
What sound driver are you using?

I'm using Sound Blaster Audigy 2 ZS and I got input to work allright using ALSA.

I did a search and found this resource.. perhaps it may be of help:
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by sparky on 2006-01-17
[QUOTE=Mr_Grieves]What sound driver are you using?

I'm using Sound Blaster Audigy 2 ZS and I got input to work allright using ALSA.

I did a search and found this resource.. perhaps it may be of help:
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)[/QUOTE]

Um, at the risk of sounding ignorant, how do I determine what sound driver I am using?

Thanks,
Sparky

---

### Post by Double A Ron on 2006-01-17
Hi Sparky,

I've been experiencing the exact same problem with my Audigy 2 Value in my Recrding Studio PC.  I get sound and I can get the line in to work on my on-board sound card (intel integrated something-or-other) but we don't want to use that POS.  I found this interesting post (regarding debian which to my understanding is very similar to Ubuntu), it's at [this other linux forum](http://www.linuxquestions.org/questions/showthread.php?t=319081).

I'm going to be trying this myself tomorrow but Id like to at least share the resource now.

It involves upgrading the Kernel and the ALSA driver.

---

