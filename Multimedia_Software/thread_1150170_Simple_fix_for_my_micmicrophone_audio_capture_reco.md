---
title: "Simple fix for my mic/microphone audio capture record issue"
date: 2009-05-05
forum: Multimedia Software
---

### Post by sadohert on 2009-05-05
Hi All.  I just did a fresh install of Jaunty.  I finally got some time to take a look at my audio capture setup because I had never seemed to get it to work quite right on my gutsy install.  I basically wanted to use the mic (aka microphone) built into my Acer monitor to capture voicemails out of my regular phone voicemail box.

I fiddled with all the different mixer settings and nothing seemed to work.  I don't quite get how the different sound servers (alsa, OSS, PulseAudio) relate to each other and to the playback and capture of audio.  I originally ignored peoples suggestions to run alsamixer from the command line figuring the gnome sound mixer exposed everything I needed anyway.  This turned out to be wrong.  Upon running alsamixer and going to the "capture" section ($alsamixer -V capture) I noticed there were 2 columns that seemed to allow me to select the input source ("Input Source" and "Input Source 1").  The options I could change this to were:
Mic
Front Mic
CD
Mix
Line

Neither was set to "Mic", which I assume is the back panel mic port on my Asus P5K-E AP motherboard.  As soon as I made the change things started to work.  I've attached a screen shot in case that helps.

I'm guessing in future if I wanted to capture audio being played by my computer (e.g., from an embedded flash player of some sort), I coudl go back in here and switch the "Input Source" to "Mix".

---

### Post by suryakalyan on 2009-05-05
Would this problem also solve voice chat problem on Empathy or Skype?

---

### Post by sadohert on 2009-05-06
If your input source(s) were not set to mic in alsamixer, I would think it would impact any program needing a mic...er... any program needing a mic that uses alsa... see... this is where I'm not clear.  Maybe you could have some other program set to make use of the OSS or PulseAudio systems, and if THEY had the "Input source" configured correctly and you still had a problem then the cause would be something else.

---

