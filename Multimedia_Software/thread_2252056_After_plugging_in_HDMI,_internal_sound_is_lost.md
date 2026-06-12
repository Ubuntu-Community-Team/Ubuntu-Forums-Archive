---
title: "After plugging in HDMI, internal sound is lost"
date: 2014-11-08
forum: Multimedia Software
---

### Post by taelus on 2014-11-08
After I plug in a monitor on HDMI (no speakers on the monitor), I lose sound output from the internal speakers on the laptop.  The card still shows up in the sound settings as "Analog Output" and it thinks it's sending a test sound to the speakers, correct speaker config, but nothing is coming through.  I checked the alsamixer to make sure nothing was muted and everything seemed fine to me.

The first time I did it, after rebooting the computer, the audio card wasn't even being detected anymore.  I had to go into /etc/modprobe.d/alsa-base.conf and add "options snd-hda-intel model=auto".  That loaded the card on a reboot, but if I plug the HDMI in, it starts all over again.

*Edit: System sounds still play, but not anything else (Spotify, VLC, etc.).*

Any ideas?

---

