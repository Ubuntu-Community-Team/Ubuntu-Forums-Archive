---
title: "External microphone not working"
date: 2011-10-08
forum: Multimedia Software
---

### Post by Alastair Rae on 2011-10-08
I'm running a vanilla 64-bit 11.04 install on a laptop. It has no internal mic and I'm trying to get an external mic to work in the sound card red socket.

I've set the sound prefs to Hardware > Analogue Stereo Duplex (as opposed to any HDMI channels) and Input has only one device Internal Audio Analogue Stereo which is selected and not muted.

None of the recording programs can hear the mic (Audacity, Sound Recorder or Skype). Any idea what else I can do?

```
$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd2600000 irq 43
```

---

### Post by Alastair Rae on 2011-11-01
Ok, I solved this after a bit of googling etc. The answer was to
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and add
```
options snd-hda-intel model=sony
```
at the end and reboot.

My sound system then sprung in to life - external mic working, and toggling between speakers and headphone on insert etc.

This seems such a common thing, I wonder why the installation doesn't do it?

---

