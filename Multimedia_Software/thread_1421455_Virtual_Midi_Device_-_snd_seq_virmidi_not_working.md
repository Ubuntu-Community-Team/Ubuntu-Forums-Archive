---
title: "Virtual Midi Device - snd_seq_virmidi not working"
date: 2010-03-04
forum: Multimedia Software
---

### Post by scotty64 on 2010-03-04
I need virtual midi devices for certain applications. The problem is that snd_seq_virmidi seems to load without any problems, but no midi devices are being created.
aconnectgui and cat /proc/asound/cards or ./devices do not list any midi device.
I tried snd_seq_virmidi both on the generic-pae kernels as well as with the realtime kernel and tried the ALSA backports version as well - not working...
Any ideas ?

---

### Post by scotty64 on 2010-03-04
Problem solved:
I loaded the wrong module - it has to be snd-virmidi, not snd-seq-virmidi.

---

