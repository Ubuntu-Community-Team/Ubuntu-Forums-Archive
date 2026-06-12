---
title: "No digital out with Audiotrak Prodigy HD2"
date: 2010-10-18
forum: Multimedia Software
---

### Post by anbello on 2010-10-18
I have an Audiotrak Prodigy HD2 sound card on a PC with ubuntu 10.10 64bit and i am not able to use the digital spdif out with pulseaudio.

With alsa i have no problems:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HD2 [Audiotrak Prodigy HD2], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HD2 [Audiotrak Prodigy HD2], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but with pulseaudio in "Sound Preferences" -> "Hardware" tab -> "Profile:" combobox i have only "Analog Stereo Input", "Analog Stereo Output" and "Analog Stereo Duplex" and no "Digital Stereo *" of any sort so i cannot use pulseaudio with spdif output.

Thanks
Andrea

---

