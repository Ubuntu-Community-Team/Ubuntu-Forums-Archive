---
title: "Pulseaudio not recognizing sound card. Showing &quot;dummy&quot; output instead"
date: 2016-10-26
forum: Multimedia Software
---

### Post by ntsirak1 on 2016-10-26
Hello,

I've searched these forums and Google and can't seem to find a solution that works for me. As stated by the subject, pulseaudio cannot detect my sound card and pavucontrol shows a dummy output as the only option. It appears that the card is visible to ALSA and the aplay command, just not pulse or pacmd. 

Here are the results of the alsa info script: [http://www.alsa-project.org/db/?f=eb51db0ac38072b7df9b93c3ff999abca3dd154c](http://www.alsa-project.org/db/?f=eb51db0ac38072b7df9b93c3ff999abca3dd154c)

I've tried deleting pulse configuration files/cookies (which weren't there anyway), adding myself to the audio group, changing permissions on various files, rebooting after all these things, and nothing has worked. Does anyone have a clue as to what's going on?

---

### Post by ntsirak1 on 2016-10-26
Solved - not exactly sure what did it but after completely removing & reinstalling alsa-base, linux-sound-base, pulseaudio, pulseaudio-module-x11, and pulseaudio-utils it works after the reboot. Very frustrating.

---

