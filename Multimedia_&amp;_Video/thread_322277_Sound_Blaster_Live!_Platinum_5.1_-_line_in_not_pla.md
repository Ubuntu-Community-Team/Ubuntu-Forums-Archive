---
title: "Sound Blaster Live! Platinum 5.1 - line in not playing through headphones"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by Dave2 on 2006-12-20
I have an SB Live! Platinum 5.1. I've been using this happily for a number of years now, with everything I've tried working. But now I seem to have thrown something at it that it can't handle: playing audio sent to it via the "line in" port on the sound card through headphones attached to the Live! Drive.

I **can** play everything else I've tried through the headphones, so it's not a problem with the headphones themselves, or with the headphone channel muted. I can play audio sent to line in via speakers (connected to the sound card) fine, too. So, I was wondering if anyone knows whether this is a hardware issue, an ALSA issue, or a PEBKAC issue?

I'm using Feisty with the 2.6.20 kernel, if that makes any difference.

(Apologies if this has been answered elsewhere - I did a fairly thorough search beforehand, and turned up nothing.)

---

### Post by deadgobby on 2006-12-20
It is just an ALSA issue. I have the same type of SC and as.
Just open up GNOME ALSA or just install it. Play with input settings.  Just double check that your line input is in the Blue on the back of the SC not the Red input.

---

### Post by Dave2 on 2006-12-20
I've already played around with alsamixer and gnome alsamixer a lot, and just tried again, with no luck. As before, I've been able to get the audio playing via the speakers, just not via the live drive-connected headphones.

The line in is definitely connected to the correct socket on the back of the sound card.

---

### Post by deadgobby on 2006-12-20
> **Dave2 said:**
> I've already played around with alsamixer and gnome alsamixer a lot, and just tried again, with no luck. As before, I've been able to get the audio playing via the speakers, just not via the live drive-connected headphones.

The line in is definitely connected to the correct socket on the back of the sound card.
Have you open up Audacity and try recording. Does it capture the sound?
Gobby

---

### Post by Dave2 on 2006-12-20
Nope. it doesn't seem to be capturing it (despite the fact that I've enabled "Line-in Capture").

Hmm... I appear to have been able to fix it with using alsamixer itself (setting "Line" to capture) - looks like the gnome alsamixer wasn't letting me set it properly. Thanks for the prompting to check capture.

---

### Post by deadgobby on 2006-12-20
Awsome. Have a good Holiday:D

---

