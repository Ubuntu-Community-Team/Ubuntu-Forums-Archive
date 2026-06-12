---
title: "Sound card not working"
date: 2008-09-06
forum: Multimedia Software
---

### Post by DrIdiot on 2008-09-06
I can't get Rhythmbox (or any other application) to play sound from my new sound card.  The module is loaded (snd-ca0106), and if I type

cat /dev/urandom > /dev/audio1 (where audio1 is my sound card)

it plays static through my speakers, so it's just that I can't get applications to play to the sound card.  However, the applications do play through my on board audio.  When I go to alsamixer, the controls for CA0106 (sound card) are displayed.

Does anyone know what the problem might be?

---

### Post by jdkoola on 2008-09-06
1. Are you by any chance using SPDIF on your soundcard?  You usually have to enable that in alsamixer (it's the IEC958 option)

2. Have you tried going into the "Sound" controls in Settings->"Settings Manager"  I think that also displays all your sound devices

---

### Post by DrIdiot on 2008-09-06
I got it to work by going to Preferences->Sound and then setting everything from "Autodetect" to "ALSA".  Will this have bad side effects?

---

### Post by DrIdiot on 2008-09-07
> **jdkoola said:**
> 1. Are you by any chance using SPDIF on your soundcard?  You usually have to enable that in alsamixer (it's the IEC958 option)

2. Have you tried going into the "Sound" controls in Settings->"Settings Manager"  I think that also displays all your sound devices

New problem: sound in Firefox, Epiphany and WINE still don't work.  However, in Totem and Rhythmbox it does work.

---

