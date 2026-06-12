---
title: "Logitech USB Headset - record levels too low"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by richardq on 2007-02-03
I've got a Logitech 250 USB headset. I'm having trouble with two things:

1. The mic level seems very low. With max input level, normal speech is at about -40dB. If I shout I can get it up to -20dB or so. I have the same problem with ffmpeg while recording a screencast. The sound is clear (and background noise is low) but I need to get higher levels. Any idea on how to boost it? Is there a universal system-wide setting? (The Gnome volume controls are all unmuted and maxed out as well).

2. I can't get the headset to playback normal sound from xmms, banshee or moc. It does play back sounds I record in Audacity and in ffmpeg, but not sounds from mp3 files and the like. Any idea how to get these things working as normal system headphones? I find the System->Preferences->Sounds dialog to be a little confusing and the documentation seems outdated.

---

### Post by richardq on 2007-02-03
I found the solution to No.1: I didn't see that 'Change Device' under the File menu in the Gnome sound mixer dialog. I changed the device to USB Headset and noticed immediately that the record level slider was way down. Boosted that up and now Audacity and ffmpeg levels are much much better. 

Still troubled with figuring out No. 2. though.

---

