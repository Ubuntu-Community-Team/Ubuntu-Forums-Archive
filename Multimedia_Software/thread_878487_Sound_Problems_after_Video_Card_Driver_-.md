---
title: "Sound Problems after Video Card Driver -"
date: 2008-08-03
forum: Multimedia Software
---

### Post by medico1849 on 2008-08-03
I installed Kubuntu 8.04 through Wubi and everything went smoothly. There was sound present on first book, however, I then installed the drivers for my nVidia 8800GT and my sound does not work.

Here is the code from terminal about the sound drivers:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
eric@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC885

My motherboard is a Gigabyte GA-EP35-D3SL.

In the mixer, all volumes are all the way up and none are muted. I've read through many other threads on sound issues and nothing works or is applicable. If anyone has any suggestions, please let me know.

---

### Post by Yellow Pasque on 2008-08-03
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by medico1849 on 2008-08-03
I seem to be lost. :confused:
After putting in lspci -v in the terminal, the soundcard portion is:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at ea100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

When I go to the link for the Alsa matrix, there isn't a dropdown box to find my chipset manufacturer. Even from Alsa's main page I can't seem to find what I need: 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Inte](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Inte)

Thus, when I try "sudo modprobe snd-", I don't have a driver to put after snd-. 

I'm going to try and disable the video driver for a while and see if things change. 

Any help would be appreciated!

---

### Post by Yellow Pasque on 2008-08-04
Your sound driver is snd-hda-intel

---

