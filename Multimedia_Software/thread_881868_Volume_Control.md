---
title: "Volume Control"
date: 2008-08-06
forum: Multimedia Software
---

### Post by elevan on 2008-08-06
In ubuntu, I have to crank my speaker dial to max to get a medium level of volume out of the speakers, whereas in Windows I barely get to 1/5 of the max volume and it's at a medium level.

Is there somewhere I can tweak the base volume setting so that my speakers aren't cranked?

School me, plz!

---

### Post by dannyboy79 on 2008-08-06
> **elevan said:**
> In ubuntu, I have to crank my speaker dial to max to get a medium level of volume out of the speakers, whereas in Windows I barely get to 1/5 of the max volume and it's at a medium level.

Is there somewhere I can tweak the base volume setting so that my speakers aren't cranked?

School me, plz!
if you double click on the speaker (volume control) is it set to PCM or something else? I know mine has to be set to pcm. also, there's a volume control on the computer (top right corner) but you're also using a volume control for your external speaker set. is the volume control on your desktop turned way down?

---

### Post by elevan on 2008-08-06
Yeah, the volume is maxed out in the volume control.  In the preferences, I have this list of options for devices to track/control:

HDA Nvidia (alsa mixer) <- current setting
Realtek ALC882 (OSS mixer)
Playback: ALSA PCM on front:...
Capture: Monitor Source of ALSA PCM on front:...
Capture: ALSA PCM on front:...

Then the settings under HDA Nvidia gives me any one of audio options that I assume are the different types of output for surround, front out, and the different types of speakers for surround.

Right now it's set to 'master' under HDA Nvidia.

---

### Post by dannyboy79 on 2008-08-06
> **elevan said:**
> Yeah, the volume is maxed out in the volume control.  In the preferences, I have this list of options for devices to track/control:

HDA Nvidia (alsa mixer) <- current setting
Realtek ALC882 (OSS mixer)
Playback: ALSA PCM on front:...
Capture: Monitor Source of ALSA PCM on front:...
Capture: ALSA PCM on front:...

Then the settings under HDA Nvidia gives me any one of audio options that I assume are the different types of output for surround, front out, and the different types of speakers for surround.

Right now it's set to 'master' under HDA Nvidia.
try changing to master to PCM.

---

