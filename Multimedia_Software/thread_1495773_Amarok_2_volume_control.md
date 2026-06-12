---
title: "Amarok 2 volume control"
date: 2010-05-28
forum: Multimedia Software
---

### Post by emeraldchen on 2010-05-28
Hi, yesterday I installed ubuntu 10.04 (64-bit) and ran into a problem with amarok 2. I can't use the ubuntu volume control when I configure phonon to use spdif or digital out of my soundcard. The only way to change the volume is to adjust it directly in amarok.
Is there a way to tell amarok to use the default ubuntu soundmixer instead of a specific device ?

Amarok finds 5 Intel HDA devices (ALC633 Digital / ALC633 Analog / ALC633 IEC958 / 2x NVIDIA HDMI ) PulseAudio and Jack Audio, but each device seems to claim the spif or the analog out, prevents the functionality of the system volume control and blocks all other applications from using it (e.g. not possible to watch youtube videos during amarok playback).

Does anyone know a solution for this problem ?

By the way, sorry for my english :)

Best regards
emeraldchen

---

### Post by emeraldchen on 2010-05-31
Is there nobody who has an idea how to deal with this problem ??

---

### Post by miguel_mips on 2011-01-28
Same here. I ran into this yesterday. 
I had sound going to HDMI and working well. After Amarok installation, had to install the ffmpeg thing and all was fine. The next day, after a system update, I started having the behaviour described above: no sound on the system in general (at least through HDMI) and amarok had sound control independent of the system, even in mute.
Rebooting didn't change anything.
Rebooting into older grub option brought system sound back but amarok still independent.
Rebooting back into most recent grub option, left me with working sound but independent amarok.
Now running clementine, which doesn't come in the repositories(!?)

---

