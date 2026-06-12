---
title: "No sound after plugging in HDMI"
date: 2010-08-02
forum: Multimedia Software
---

### Post by rschnitzel721 on 2010-08-02
The computer is an ASUS g50v.  I tried plugging it into my tv via the built in HDMI and now my sound won't work.

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v - audio:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a3
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I have double checked that alsamixer is not muted and have done a clean install of my drivers.  I don't know where to go from here.  

Thanks for the help in advance.

---

### Post by chenxiaolong on 2010-08-02
This is a simple question, but have to selected the HDMI device in the pulseaudio preferences (System > Preferences > Sound Preferences)?

Screenshot attached.

---

### Post by rschnitzel721 on 2010-08-02
I have selected the HDMI device and then rebooted my computer, but I still don't have sound.  

I also don't have sound if I try to change my sound back from HDMI and reboot.

If it helps I do get the ubuntu load screen sound from my computer speakers no matter what device I have selected in pulse audio.

---

### Post by chenxiaolong on 2010-08-02
That's really strange. Normally, I plug in my HDMI cable to my TV and my laptop (Dell Studio 1555 with the same Intel ICH9 chipset as your computer), I choose the HDMI setting in the pulseaudio preferences and then the sound magically works. I don't know what could be the problem.

EDIT: I just noticed that your HDMI output is from your NVidia card. Make sure you're running the latest NVidia proprietary driver (System > Administration > Hardware Drivers). The older drivers are known to have problems with HDMI audio.

---

### Post by bprins on 2010-08-07
managed to solve this already?

if not, which version of alsa are you running?

```
cat /proc/asound/version
```

if it's not 1.0.23 then that would be my first suggestion. if you need help upgrading to 1.0.23 let me know.

---

### Post by chenxiaolong on 2010-08-07
Here's an alsa upgrade guide if you still have the problem: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

