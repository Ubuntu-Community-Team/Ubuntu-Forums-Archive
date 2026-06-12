---
title: "Creative Xmod and mixer problems with pulseaudio (11.10)"
date: 2011-11-22
forum: Multimedia Software
---

### Post by QuantikTar on 2011-11-22
Until now, I was using this USB soundcard successfully. It was always recognized as a 5.1 device (even if it has only a stereo output) but after applying this [workaround]("http://springpadit.com/swsetiadi/note/settingupcreativexmodinlinuxmintpulseaudio") (second tip) on Natty, everything worked fine.

But now on Oneiric, this tip is not working anymore. When I modify /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf and restart pulseaudio, my custom profile is not appearing on the sound card properties.

I tryed to use UDEV variable (PULSE_PROFILE_SET) with my usb vendor/device ID to specify a custom profile file, but this is also not working. (still no Xmod profile in custom properties).hat 

Any Idea?

(Or if someone has another solution to make the volume control working correctly between pulseaudio and alsa with this card, I take it too! For the moment this is catastrophic, I made so much tests that the sound is playing only in my right speaker, sniff...)

Thanks

---

### Post by QuantikTar on 2011-11-30
Any idea?

Thanks

---

