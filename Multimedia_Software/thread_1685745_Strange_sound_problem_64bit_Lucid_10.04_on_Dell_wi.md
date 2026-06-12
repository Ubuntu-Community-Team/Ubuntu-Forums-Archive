---
title: "Strange sound problem 64bit Lucid 10.04 on Dell with Intel HDA"
date: 2011-02-11
forum: Multimedia Software
---

### Post by arpoodle on 2011-02-11
Up until a couple of weeks ago, I had sound on my Dell XPS17, no problem.

Now, nothing. 

I've checked alsamixer and nothing's muted

Output of various stuff is as follows:

```
root@hiro:~# dmesg | grep -i HDA| cat
[   19.439991] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.440127] HDA Intel 0000:00:1b.0: setting latency timer to 64
root@hiro:~# lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:cbefc000-cbefffff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f0c00000-f0c03fff
root@hiro:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@hiro:~# dpkg -l | grep alsa
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libsnack2-alsa                                 2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
ii  linux-alsa-driver-modules-2.6.32-27-generic    2.6.32-27.201101301600                          Ubuntu-supplied Linux modules for version 2.
root@hiro:~# dpkg -l | grep pulse
ii  gstreamer0.10-pulseaudio                       0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  libpulse-browse0                               1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainloop-glib0                        1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (glib support)
ii  libpulse0                                      1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries
ii  libsdl1.2debian-pulseaudio                     1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
ii  pulseaudio                                     1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio sound server
ii  pulseaudio-esound-compat                       1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio ESD compatibility layer
ii  pulseaudio-module-x11                          1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 X11 module for PulseAudio sound server
ii  pulseaudio-utils                               1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Command line tools for the PulseAudio sound 
root@hiro:~# 

```

Any ideas?

---

