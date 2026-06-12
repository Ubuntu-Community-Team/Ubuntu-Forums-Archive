---
title: "Volume Buttons on a Dell Inspiron 1720 control wrong channel."
date: 2009-05-08
forum: Multimedia Software
---

### Post by tompickles on 2009-05-08
I have recently installed 9.04 - fab release - credit to all involved.
One really annoying niggle though, is the media control buttons on the front of my laptop correctly show up the relevant notification (i.e. Volume Up/Down or Mute) but they seem be controlling the "Capture: HDA Intel - STAC92xx Analog (PulseAudio Mixer)" channel rather than the, what I assume would be the correct, "HDA Intel (Alsa mixer)" which is the device which changes when I use the Volume Control in the Panel.

Any ideas how I can change which device the media buttons relate to?

Thanks for any advice in advance.

---

### Post by pbrane on 2009-05-09
I had the same problem when I installed Jaunty on my Inspiron 1720. Intrepid worked fine. I solved this by changing the Default Mixer Tracks in System->Preferences->sound to the Playback HDA Intel device.

---

### Post by tompickles on 2009-05-09
Fab - thank you! Worked a charm.

---

