---
title: "alsa on Ubunbtu 8.04"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by Sergeant_Pony on 2008-04-04
Hi,
I'm running Ubuntu 8.04 beta on a Toshiba Satellite Laptop. I have sound working fine except that I cannot adjust the volume from the desktop. I have to use the "wheel" on the front of the laptop itself. I also noticed that on the upgrade from 7.10 Alsa disappeared and I only have OSS.
Is there a way to get alsa (alsamixer) etc... back? and is there a way to fix the volume issue?

Thanks
Sergeant_Pony

---

### Post by Phil Urich on 2008-04-05
I'm having a potentially-related problem, in that I can no longer control volume and it sounds terrible, although I still have alsamixer as a binary, just when I try to run it the complaint is:

```
alsamixer: function snd_mixer_load failed: No such file or directory
```

I did a purge+reinstall, going to see if that does anything but I'm doubting . . . hopefully this is just a bug that'll be fixed by the time Hardy itself is released.

Edit: to clarify, I normally use KDE, and in KDE one can move the sliders but they instantly jump back to 100%.  I have GNOME installed too (I'm a bit of a desktop environment dweeb) and there it behaves like Sergeant_Pony described.

In case it's useful, here's the info I can get about my sound card (I have a generic Centrino-based laptop):

```
chalker@pegasus:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

