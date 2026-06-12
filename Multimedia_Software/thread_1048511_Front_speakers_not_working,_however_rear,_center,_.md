---
title: "Front speakers not working, however rear, center, lfe works fine"
date: 2009-01-23
forum: Multimedia Software
---

### Post by Gorstak on 2009-01-23
I freshly installed Linux and tried to set sound card. I followed instructions from [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support](http://ubuntuforums.org/showthread.php?t=789578) and edited /etc/pulse/daemon.conf to change default-sample-channels = 6 (before editing I had only front speakers working). Now other channels other then front works fine but front remains silent ?!?

---

### Post by markbuntu on 2009-01-23
Have you checked the volume sliders in all the volume controls?

---

### Post by Gorstak on 2009-01-23
It's working now, I have two nearly identical sound cards and they have same name so system mixer got confused and never allow me to adjust cards precisely. I installed gnome-alsa-mixer and now I have full control.

---

