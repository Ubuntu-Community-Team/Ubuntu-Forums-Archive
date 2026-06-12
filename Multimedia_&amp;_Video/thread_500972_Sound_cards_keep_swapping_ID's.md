---
title: "Sound cards keep swapping ID's"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by Maxxarcade on 2007-07-14
I have two sound cards in a system dedicated for MIDI use, and every couple times I boot it up, the sound cards swap ID's (hw:0 and hw:1) which causes things to stop working until I change settings in the programs. 

Is there any way to manually specify which card gets hw:0 and which gets hw:1 instead of letting it configure automatically?

---

### Post by cylon359 on 2007-07-15
Yes, look in /etc/modprobe.d/alsa-base - I have something like this, that forces a certain order :

options snd-emu10k1 index=0
options snd-hda-intel index=1
options snd-bt87x index=2

Unless both your MIDI cards are USB, in which case you would need some udev magic... I don't know how to do that.

---

### Post by Maxxarcade on 2007-07-15
I'll give it a try, thanks!  

I am using an Audigy card and an old AudioPCI card (had a Live card before, but it distorted too much).

I had started with two identical Live cards, but the Alsa mixer didn't let me make independent settings for each card, even though I could select each one from the device list :confused:

Will everything be in /etc/modprobe.d/alsa-base, and I just add the index=n to each one?  I won't be able to look at it until later next week.

---

### Post by cylon359 on 2007-07-16
If there isn't an options line for your sound card driver, just add one.

If your Live card is distorting the sound and you have the bass turned up, try turning down the "Wave" control in alsamixer.

---

