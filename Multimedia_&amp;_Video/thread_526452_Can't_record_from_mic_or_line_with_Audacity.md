---
title: "Can't record from mic or line with Audacity"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by ka1ssr on 2007-08-15
I am having trouble recording with Audacity.  There's usually an input selection drop-down box between the output and input faders, but it disappeared when I upgraded to Feisty.  Alsmixer shows only a playback tab, no record tab.  I can't record from either the mic or line-in jacks.  I've downloaded and built the alsa 1.0.14 drivers from the alsa site as suggested in previous posts but that hasn't fixed the problem.  The machine is a Compaq S4000V.  The on-board audio is SiS SI7012 and the codec is a Realtek ALC650F.

Thanks in advance for any help.

Bill

---

### Post by duffrecords on 2007-08-15
Try using [JACK]("http://jackaudio.org") to connect your sound card to Audacity's inputs.

---

### Post by Amazona aestiva on 2007-08-15
After this, Audacity should record the line out?(what you hear from your speakers)
For example: If you play an avi, Audacity will record its sound.;)

In your volume control there must be something like these thumbnails.(1st,2nd)

Understand the pictures:
Lejátszás - Play
Felvétel - Record
Kapcsolók - :confused:switch:confused:
Eszköz - Device

So there must be "Felvétel" and enabled Mix!(disabled Mix -> mono record)
You can add these at edit->preferences or properties(I have "Beállítások")
NOTE: Do NOT turn "Felvétel" above mine. (try it but might be too loud)

Switch the devices ALSA or OSS which you uses.(in Audacity,3rd picture)

I'm not perfect in English. Sorry...

---

