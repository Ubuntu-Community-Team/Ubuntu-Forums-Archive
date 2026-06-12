---
title: "SPDIF output need something extra?"
date: 2010-10-16
forum: Multimedia Software
---

### Post by RealGomer on 2010-10-16
Now that I got my RT2870 wireless-n adapter to work, I'm onto another problem. I need to output the audio from my Gigabyte K8NS-Pro mobo based PC through the S/PDIF port. I ran the "aplay" command as root and the output was this:

root@Homebrew:/home/red# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@Homebrew:/home/red# 


I've seen several posts referencing a hardware tab in ALSA mixer but after I installed both it & ALSA I don't see a hardware tab. Do I need to install anything else or set any switches?

thanks!

---

