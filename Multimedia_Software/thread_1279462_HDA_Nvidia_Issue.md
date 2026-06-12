---
title: "HDA Nvidia Issue"
date: 2009-09-30
forum: Multimedia Software
---

### Post by snowx1000 on 2009-09-30
I am having an issue getting audio from all sources playing over my onboard sound HDA Nvidia(Realtek). Sound plays fine in Mplayer using alsa, but I get no sound in any other app. When trying to set defaults for sounds in gnome, picking realtek analog gives an error (could not open audio device for playback). Digital plays back nothing. After messing around with some gstreamer settings, sound events work (HDA NVIDIA Digital Custom), but still no dice on music etc. I appreciate any help.

Thanks,
Mark

Solved my own problem, went into gconf-editor and manually set the musicsink line in gstreamer to the proper alsa string 'alsasink device="hw:0,0"'

---

