---
title: "For some reason, Audacity cannot play back audio files"
date: 2008-07-16
forum: Multimedia Software
---

### Post by SilverGoldBronze on 2008-07-16
I got ubuntu, and I love it far more then windows. However, when I record in Audacity, it gives me the following message when I play back:Error while opening sound device. Please check the output device settings and the project sample rate.

;.;

---

### Post by SilverGoldBronze on 2008-07-17
Bump: Can anyone help?

---

### Post by CharmlessMan on 2009-01-30
It was working fine for me earlier. THen after I restarted after downloading some updates I get what's posted above.

---

### Post by ursaminor on 2009-02-04
I got the same message also, so I went to the Audacity website and downloaded the latest version. Audacity now plays.

---

### Post by Willberg on 2009-02-04
For some reason Ubuntu uses some sound... THING, that isn't properly compatible with Audacity, or something like that. I dunno.

Anyways; what worked for me was to start Audacity using this command:

pasuspender -- audacity

But then you can't have anything else using the sound card at the same time. Once Audacity starts for the first time, take a look at the preferences and fiddle with the sound in and sound out options to see which combination works.

---

### Post by Tuxi on 2009-02-04
> **Willberg said:**
> For some reason Ubuntu uses some sound... THING, that isn't properly compatible with Audacity, or something like that. I dunno.

Anyways; what worked for me was to start Audacity using this command:

pasuspender -- audacity

But then you can't have anything else using the sound card at the same time. Once Audacity starts for the first time, take a look at the preferences and fiddle with the sound in and sound out options to see which combination works.

Thanks for this.  I knew there was a problem Audacity had with pulseaudio.  After testing the command, I edited my menu item to launch with "pasuspender -- audacity".

---

### Post by ricardisimo on 2009-02-12
pasuspender is not working for me. Is there some newer (or older), PulseAudio-compliant version of Audacity anywhere?

---

### Post by ricardisimo on 2009-02-12
Never mind... I just removed pulseaudio and everything is working like a dream now. Can someone explain the whole pulseaudio-Ubuntu fiasco to me? Why has it been done so badly? Why do we have to move to pulseaudio if esound and ALSA are already working just fine?

---

### Post by ricardisimo on 2009-02-15
I take it back... audacity is still playing audio files at about half-speed. Weird. Everything else is fine, however.

---

