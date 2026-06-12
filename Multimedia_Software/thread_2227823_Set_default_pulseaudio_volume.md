---
title: "Set default pulseaudio volume"
date: 2014-06-04
forum: Multimedia Software
---

### Post by (O) on 2014-06-04
When I reboot, the volume on the PulseAudio sinks is set to 100%.  I know how to change the volume using pactl set-sink-volume, but that is only set temporarily.  I could write a script that is run at startup, but it will not be applied if I connect a sink later.  (i.e. a Bluetooth speaker)

Is there a config file where I can set the default volume that is given to a device when it is first loaded by PulseAudio?

---

