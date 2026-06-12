---
title: "Audio Mixer not changing volume"
date: 2011-09-13
forum: Multimedia Software
---

### Post by bpcrshooter15 on 2011-09-13
Hi, I've run into an issue in 11.04 where my audio works, however adjusting the volume slider or mixer doesn't change the actual volume unless I put it at 0 in which case it will mute the sound. So I have either muted sound or full blast.  any thoughts on how to correct the issue?    I have a E-MU tracker pre USB sound card and all other settings are default.  Everything worked fine in previous versions of Ubuntu. thank you

---

### Post by MrSpike16 on 2011-09-13
Welcome to the wacky world of Alsa.

Install GNOME ALSA Mixer.  Run it and move the volume control in the Panel.  On mine the Master control in GNOME ALSA Mixer moves in sync but the PCM doesn't move till Master hits 0, then PCM drops to zero.

Sounds like yours is doing the same, which gives you max volume or muted only.

Try putting the Master near max and adjusting the PCM.  Only use PCM for adjusting level.

---

### Post by bpcrshooter15 on 2011-09-16
Tried that.  Tried everything I could think of.  I ended up trying 10.04 again where it used to work, but the same problem occurred there.  I haven't changed any hardware.  I finally just ran a copy in VM and the problem was fixed there.  I would still appreciate a solution for the native scenario.

---

### Post by MrSpike16 on 2011-09-17
Did some more searching and found that this is not a bug, but is now normal behavior for PCM.
PulseAudio (system sound server) is maxing out the PCM as part of it's new method to set proper audio levels.  You can read about it here:_[http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes](http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes)_[]("http://pulseaudio.org/wiki/PulseAudioStoleMyVolume") , but basically they are dumbing down audio control to benefit the "average" computer user.

The best workaround appears to be to unlink the PCM control.  This will allow you to set the PCM level and using the panel volume control won't change it.  Also rebooting computer won't change PCM back to max either.
Need to edit a configuration:
```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```Under ```
[Element PCM]
``` look for ```
 volume = merge
``` and change it to ```
volume = ignore
```Save and then reboot computer for change to take effect.  Works for me and hopefully for you.

---

### Post by bpcrshooter15 on 2011-09-17
Thank you for the response.  Once I re-install the OS I'll give it a shot.  I see the explanation but that implementation(or lack of transparency on the "issue") is kind of annoying, especially to the non-everyday Linux user. anyhow, thank you again.

---

### Post by BicyclerBoy on 2011-09-17
This is probably irrelevant with your setup..

But that behaviour is correct/normal if you were using digital pass-thru' over S/PDIF..

There was an issue with pulseaudio resetting the default volume levels on reboot (10.04) but that was ~2 yrs ago.

---

