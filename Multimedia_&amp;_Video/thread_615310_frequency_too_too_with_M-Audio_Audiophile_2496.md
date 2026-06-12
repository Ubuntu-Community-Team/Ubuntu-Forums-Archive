---
title: "frequency too too with M-Audio Audiophile 2496"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by violinchris@gmail.com on 2007-11-16
I have a M-Audio Audiophile 2496 sound card.  The sound output is slightly less than a whole step flat.  That is the problem.  Some other threads led me to install the Envy24 control and later to enable the same sort of options available in the Envy24 control in the gnome-volume-control through the preferences.  With either of these I could affect the frequency of the output, but never in a way that made it right.  For example, I could set the clock rate to 96000 for the chipmunk version, or 22050 for something resembling whale song.  Obviously I have tried 44100.  Oddly enough 44100 and 48000 give the same result, which again is approximately a whole step low.  I have tried locking the sample rate also to see if that made a difference.  I am running a recently installed Ubuntu 7.10.  

One other piece of info, I was running Mandriva 10.2 with the card working fine, that is, with the correct  frequency output, though I really don't know if I was running alsa on the mandriva or not.  Point being I don't think anything is wrong with the card.

Thanks for any help.

Chris

---

### Post by Yellow Pasque on 2007-11-17
M-audio cards are officially supported under OSS. Try removing ALSA and installing that instead (see my sig).

---

### Post by violinchris@gmail.com on 2007-12-03
i changed a line in /usr/share/alsa/alsa.conf from

defaults.pcm.dmix.rate 48000

to

defaults.pcm.dmix.rate 44100



this worked for me.  now the output is at the right frequency.  anyone with more knowledge feel free to explain this, or better yet, why it was necessary.

---

### Post by violinchris@gmail.com on 2008-05-12
thought i would follow up.  i just did the Hardy upgrade and my same problem with the frequency being too low returned.  the same fix that worked earlier worked again.  in addition, i also had the pop/click problem that i read about and changing the sound output settings by going to System -> Preferences -> Sound worked for the pops.  hope this helps someone and i hope this gets fixed.

---

