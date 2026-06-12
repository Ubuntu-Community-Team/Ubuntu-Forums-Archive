---
title: "How can I pass audio to two sound cards at the same time with ALSA?"
date: 2011-02-13
forum: Multimedia Software
---

### Post by stee on 2011-02-13
I have an internal sound card at hw 0:0, connected to my stereo with analog (2.0) cables and an NVidia HDMI output at hw 1:7. 

My system is an ASUS EB1501P, by the way, and I'm using Ubuntu 10.04 with the latest updates (since my remote control doesn't work with LIRC in 10.10). I have however updated ALSA to 1.0.23 through backports. I also removed pulseaudio because it ****** things up.

Currently, I've set up the sound to go to the hdmi output only, but it would be great if I could make it go to both at the same time, or be able to pick which one I would like to use through a GUI. 
My current alsa.conf is exactly like in post #3 in [this link]("http://ubuntuforums.org/showthread.php?t=1620926").

[This link]("http://alsa.opensrc.org/.asoundrc#Dupe_output_to_multiple_cards") seems to give an example, but it seems complicated to me and isn't quite well explained.

---

