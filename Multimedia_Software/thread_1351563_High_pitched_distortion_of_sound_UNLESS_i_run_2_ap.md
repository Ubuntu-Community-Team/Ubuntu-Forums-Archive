---
title: "High pitched distortion of sound UNLESS i run 2 apps at once"
date: 2009-12-10
forum: Multimedia Software
---

### Post by jotto! on 2009-12-10
Im having trouble with my sound. I have a 5.1 speaker setup but am getting a high pitched distortion on all sounds.
If I change to mono, stereo or 4.0 speaker setup, the sound is perfect with no distortion.
As soon as I change to 4.1, 5.0 or 5.1 it appears.

I have just found that if I open rhythmbox and play an audio file and then open totem and play another audio file the sound becomes perfect again. If I mute one of the applications, again the sound stays perfect.
As soon as I close down one of the running apps, the distortion is back!

Any ideas? could it be a driver issue or something of that nature?
[B]Would I be using pulse or alsa drivers as standard?
[/B] 
Im running 9.10 fully up to date and my sound is onboard, VIA 8237.
TIA.

---

### Post by joes7 on 2009-12-10
Have you tried by changing the input sound device? Also, browse through the setting options, you'll find it there.

---

### Post by jotto! on 2009-12-11
Yeah, tried various settings all of which didnt work.

I now have **uninstalled** pulse and am running alsa. If I do a speaker test I can hear sound only from the fronts.

If I add the command ( cant remember exactly  but something like ) dplug 5.1 I hear sound through all speakers.

How can I set alsa to 5.1 as default please.

---

