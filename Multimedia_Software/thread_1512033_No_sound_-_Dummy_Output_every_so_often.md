---
title: "No sound - Dummy Output every so often"
date: 2010-06-17
forum: Multimedia Software
---

### Post by Lokiii on 2010-06-17
So, this is a very strange problem.

Im running Ubuntu 10.04 x64. Audio worked fine until some kernel updates (cant remember which one). Then after rebooting, my audio devices werent being detected and audio preferences only gave me a "dummy output". I also noticed that I coulndt reboot or shutdown the computer normally as it would just throw me back to the login screen, so I had to reboot through sudo shutdown -r now. 

Anyways, I got back in and audio was working again and so was shutdown and rebooting as normal. However, after the next reboot sound was gone again.

So I tried removing the kernel that was installed, but that didnt help. It just seems very random and I find it strange the shutdown/reboot issues follows it. 

So, anyone have any idea on whats wrong?

Kind Regards

---

### Post by narcisgarcia on 2010-06-28
I lost the sound output when I was working with Ubuntu 9.10 (the volume applet showed "Dummy Output"), and I thought upgrading to Ubuntu 10.04 might help, but today I've done the upgrade and no instant result about audio matter.

Running [aplay -l]("http://ubuntuforums.org/showthread.php?t=1475185") in a terminal this is my result:
> **** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And then I've clicked on the volume indicator, selected Sound Preferences, and gone to the Hardware tab. Where I see "Internal audio" in the devices list, I've selected the first "Internal audio" and choosen "Analog Stereo Output" in the dropdown, and then I've choosen the second "Internal audio" and choosen "Analog Stereo Input".

Since this moment the volume applet indicates the output level, and all the programs reproduce audio again.

---

