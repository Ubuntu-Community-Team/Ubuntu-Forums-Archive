---
title: "No sound - Ubuntu 11.04, Intel Series 6 HD audio"
date: 2011-09-07
forum: Multimedia Software
---

### Post by chortlebuffer on 2011-09-07
Hi all,

Just put together a machine that gives audio fine for Windows. No sound on Ubuntu unfortunately. My details are here (alsa project output)

[http://www.alsa-project.org/db/?f=1934ac719fc70c2da71ee8dc8cba5ce67eccba2c](http://www.alsa-project.org/db/?f=1934ac719fc70c2da71ee8dc8cba5ce67eccba2c)

The motherboard is an Asrock z68 extreme 4. Two crossfired Radeon XFX 6950 graphics cards. I wonder if the graphics cards built in audio (I think they have it) is killing the audio from the motherboard (intel series 6 HD audio)?

---

### Post by .... on 2011-09-08
First off, use this to update PCI Id's, to make hardware id easier:
```
sudo update-pciids
```Something's wrong with the kernel module. Try this: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

> I wonder if the graphics cards built in audio (I think they have it) is killing the audio from the motherboard
They don't have any kernel modules loaded either. At any rate, the onboard is the default audio device.

---

