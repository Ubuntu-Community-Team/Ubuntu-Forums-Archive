---
title: "Kubuntu 9.10 sound issues"
date: 2010-01-31
forum: Multimedia Software
---

### Post by Hatfieco on 2010-01-31
So I just used WUBI to try out kubuntu on a sony vaio FE-790p. Everything was fine and dandy until I started reading on how to install flash for firefox, which now works. In the process I lost sound, no streaming audio sound, but I do have a startup and shutdown tone. I also have the ability to test the sound output from the HDA intel portion but the Pulseaudio driver says that it is unable to start and its falling back to the intel set? Any help would be great. Thanks.

---

### Post by sports.car.guy on 2010-01-31
> **Hatfieco said:**
> So I just used WUBI to try out kubuntu on a sony vaio FE-790p. Everything was fine and dandy until I started reading on how to install flash for firefox, which now works. In the process I lost sound, no streaming audio sound, but I do have a startup and shutdown tone. I also have the ability to test the sound output from the HDA intel portion but the Pulseaudio driver says that it is unable to start and its falling back to the intel set? Any help would be great. Thanks.

Why did you install PulseAudio onto Kubuntu??? There is no need for it and probably the whole reason why you are dealing with what you are. Flash works fine for me on Kubuntu without PulseAudio out of the box only using Alsa.

Remove PulseAudio client / server including config files with your package manager and I bet things will improve.

---

