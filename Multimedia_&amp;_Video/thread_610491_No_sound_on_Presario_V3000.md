---
title: "No sound on Presario V3000"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Fuqaha on 2007-11-12
Hi friends,

I am really new to Ubuntu and just installed Gutsy on Compaq Presario V3000. Everything works really well, even the WiFi works out of the box! 

But the only issue is there is no sound at all. I mean, no sound from startup till shutdown.

Based on this link:
[http://www.linlap.com/wiki/HP-Compaq+Presario+V3000z](http://www.linlap.com/wiki/HP-Compaq+Presario+V3000z)

It says "Use the snd-hda-intel driver".

Can anyone help me out on achieving this? Thank you in advance.

=)

*note : ive tried Fedora 8 too, the sound functions well, but seems that Fedora is quite a hassle for me, I think I might stick with Ubuntu.

---

### Post by Metaljaz on 2007-11-12
If you haven't already tried this:

Right click on the volume control icon (top right corner) click preferences and make sure you have the device set to Intel ICH5(Alsa Mixer). Try setting the track to control to PCM and see what happens.

Double-click the volume icon and check under file>change device and make sure it is set to the same thing. Make sure PCM is not muted but mute PC Speaker. Then try the volume slider on the panel.

Just suggestions....

---

