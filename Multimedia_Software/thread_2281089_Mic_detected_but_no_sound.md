---
title: "Mic detected but no sound"
date: 2015-06-04
forum: Multimedia Software
---

### Post by Innuend0 on 2015-06-04
Hello everybody,

I bought a headset to be able to do videoconferences. But I can't manage to use the mic on Ubuntu 14.04.1. I already tried many things without success.

The mic in itself is working (while playing with alsamixer I was able to hear my voice directly in the headset).

The headset is plugged on the dock (I tried both input/output unified with an adaptor and separated). The alsamixer "Dock Mic" is at 100. The sound options show that the mic is detected (I can see the corresponding label appearing and disappearing when I plug in/out the mic). 

But no sound is detected by the system. In the sound options, the level mark for the input always stays stuck at 0. Same thing with Skype.

I tried to configure and play with alsamixer, pavucontrol and hdajackretask without success. I put everything back to default to keep a clean config.

Does anybody has any lead ?

Thanks in advance :smile:

---

### Post by dino99 on 2015-06-05
the latest used pulseaudio is very hardware sensitive: check that the jacks are plugged where they have to be, and bios set to 'hda' not 'ac97'; then pavucontrol (both 'configuration' & then 'output devices' tabs) might help to select/adjust the good options.

---

### Post by Innuend0 on 2015-06-05
Thanks for your answer.

> check that the  jacks are plugged where they have to be

I don't really understand. If the "Dock Mic" label appears when the mic is plugged in shouldn't this be OK ? Or am I missing something ?

> and bios set to 'hda' not  'ac97'

There doesn't seem to be such an option in my BIOS. Is there a way to configure/verify the parameter from the OS ?

> then pavucontrol (both 'configuration' & then 'output  devices' tabs) might help to select/adjust the good options.

The Input Devices tab seems to be OK : Dock Microphone (plugged in), sound  at 100%.
How the Configuration tab is supposed to look ? I have two entries Built-in Audio. One for HDMI (Off) and one for Analog (Analog Stereo Duplex).

---

