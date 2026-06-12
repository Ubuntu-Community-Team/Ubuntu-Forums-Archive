---
title: "No Sound Devices Detected"
date: 2011-01-15
forum: Multimedia Software
---

### Post by CosmicFlux on 2011-01-15
Hey,

I tried to install the latest RealTek driver for Linux and it has wiped all my devices. 

I've tried reinstalling the alsa-base packages but it hasn't worked

:-z

---

### Post by BicyclerBoy on 2011-01-16
What do you mean by latest RealTek drivers ???

All linux audio device support comes from the alsa kernel modules.
These can be updated by compiling kernel modules & installing.

Did you do this ?
Why?

The best way to you to recover is to re-install the linux kernel package.

There are later kernels you can easily install to get updated alsa modules.

---

### Post by lidex on 2011-01-16
Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by CosmicFlux on 2011-01-16
```
Reading state information... Done
E: Unable to locate package reinstall
E: Unable to locate package linux-ubuntu-modules-2.6.35-24-generic
E: Couldn't find any package by regex 'linux-ubuntu-modules-2.6.35-24-generic'

```

I downloaded the Realtek drivers for Linux from their site because I'm having sound issues with the current ones I have. My sound is Realtek ALC883.

---

### Post by CosmicFlux on 2011-01-17
I managed to sort it out by upgrading my linux kernal modules

---

