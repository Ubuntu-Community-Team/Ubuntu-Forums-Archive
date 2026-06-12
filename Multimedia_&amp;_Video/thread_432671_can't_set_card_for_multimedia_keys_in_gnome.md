---
title: "can't set card for multimedia keys in gnome"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by ferenc on 2007-05-04
My multimedia keys (volume up/down, mute) insist on controlling card #0, no matter what I set in System -> Preferences -> Sound / Default Mixer Tracks.  Changing the track (Master, PCM, etc) controlled by the multimedia keys works fine.

I checked with gconf-editor that when I change the device (or the track) in the System -> Preferences -> Sound gui, the Gnome config settings under desktop/gnome/sound seem to change correctly, for both default_mixer_device and for default_mixer_tracks.  The default_mixer_device gets set to either "alsamixer:hw:0" or "alsamixer:hw:1", but it has no effect; the buttons control device #0 no matter what.

This issue is quite annoying, because the sound cards get assigned in a random order, so card #0 is sometimes one card, sometimes the other.  Any suggestions?

(I am using feisty, with an on-board VIA 8237 and a PCI CMI8738 card.)

---

### Post by ferenc on 2007-05-05
OK, figured it out:
 1. If you have a ~/.asoundrc file, the volume buttons control the pcm.!default device specified there instead of what's in System -> Preferences -> Sound.  This is probably a bug.
 2. When you change the track, it takes effect immediately (after you close the Sound dialog), but when you change the device, you need to restart X for this to take effect.

Anyway, I removed my ~/.asoundrc, set the default device in the Sound dialog, and restarted X -- now everything is working fine.

---

### Post by ferenc on 2007-05-17
Just for the sake of posterity, and then I'll stop talking to myself:

That did not work, either; in the end, I followed Juan M. Triana's suggestion ([see here]("http://code.campware.org/phorum/read.php?20,5531,5541#msg-5541")) on the Campcaster support list, and that finally worked.

---

