---
title: "[SOLVED] Turtle Beach Riviera spidf 5.1 help"
date: 2008-09-08
forum: Multimedia Software
---

### Post by speed32219 on 2008-09-08
It took me a while to get the spidf otpical working in stereo.

For the life of me I can not get it to pass ac3 5.1 over the toslink, it sends it in stereo.  In Mplayer on the side bar under properities when movie is playing, it shows AC3 and 5.1  under sound.  But if I go into audio (Mplayer)under preferences while the movie is playing it shows 5.1 not AC3 passthrough.  Using VLC or any other movie playback SW it displays only stereo.  Somewhere I need to add ac hwa3 (I think).  

Again, Stereo on spidf optical but no ac3 passthrough.

Installed Pulse and all the lib's that go with it for Alsa.  Also made change to /etc/pulse.conf (I think) and in system/preference/sound changed everything to pulse.  In alsamixer I have IEC958 output unmuted. Mplayer and Xbmc are now working using AC3 passthrough.  But VLC and Movie player are sitll in stereo.  GO figure.

---

