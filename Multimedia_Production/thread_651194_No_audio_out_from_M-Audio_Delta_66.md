---
title: "No audio out from M-Audio Delta 66"
date: 2007-12-27
forum: Multimedia Production
---

### Post by chunderbunny on 2007-12-27
Hi guys.

I'm having some trouble with a fresh install of UbuntuStudio (7.10) and and my M-audio Delta 66.

I've used the envy24 Control Utility to unmute all the channels and raise the volume. In the Patchbay section I have PCM 1 and 2 routed to hardware out 1 and 2. 

In Audacity I have set the playback device to "ALSA: M Audio Delta 66: ICE1712 multi (hw:0,0)"

Playing a track in Audacity causes a signal to be seen on the envy24 control panel on the PCM out 1 and 2 channels (and also on the Digital Mixer channel), however no audio comes out of the actual Break out box. 

I also get no signal from the SPDIF IN/OUT, not even a clock signal.

The card works fine in Windows XP, so I'm fairly certain it's not a hardware issue. Any tips?

---

### Post by chunderbunny on 2007-12-27
After digging around on the Internet I've discovered this is a known problem with the latest version of Delta 66 card (revision E), see this thread at the  ALSA bugtracker for details:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327)

---

