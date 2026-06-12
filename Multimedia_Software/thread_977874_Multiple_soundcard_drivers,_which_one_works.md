---
title: "Multiple soundcard drivers, which one works?"
date: 2008-11-10
forum: Multimedia Software
---

### Post by cov on 2008-11-10
I have installed 8.10 from scratch, but find I have several options for soundcard drivers:

See attached screenshot.

If I type:
'aplay -l' I get the following response:
```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm convinced that there are conflicts on my system which is preventing my sound card from working.

I have followed the instructions in the Sound Sticky, but am unable to resolve my problem.

Similarly, I have posted numerous times with no response.

My system is AMD64 Shuttle with an onboard Nvidia sound, and a soundblaster Live! 24 Creative Labs SB Audigy LS

'lspci -v' gives the following:
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3585
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Memory at ef001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 1006
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```

Can anyone help?

---

### Post by cov on 2008-11-11
Does this offer a hint?

From /var/logs/messages:```
Nov 11 07:53:20 Gimli pulseaudio[6052]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 11 07:53:20 Gimli pulseaudio[6054]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 11 07:53:20 Gimli pulseaudio[6054]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 11 07:53:20 Gimli pulseaudio[6054]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 11 07:53:20 Gimli pulseaudio[6054]: alsa-util.c: Cannot find fallback mixer control "PCM".
Nov 11 07:53:20 Gimli pulseaudio[6054]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 11 07:53:20 Gimli pulseaudio[6054]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 11 07:53:45 Gimli kernel: [  110.604713] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by kostkon on 2008-11-11
Wait. Do you mean that you have two soundcards but you don't get any sound?

You could install the *PulseAudio Device Chooser*. This will allow you to set the default audio device for your system and/or which device (i.e. soundcard) each of your applications will use to output their sound, etc.

You will need to set your outputs in *Sound Preferences* (*System -> Preferences -> Sound*) to *Autodetect*.

Having two soundcards does not mean that there will be a conflict. You just have to set one of them as the default.

You can easily have as many audio devices (soundcards, usb headsets, etc) as you want in your system. It does not matter.

---

### Post by cov on 2008-11-11
> **kostkon said:**
> Wait. Do you mean that you have two soundcards but you don't get any sound?

You could install the *PulseAudio Device Chooser*. This will allow you to set the default audio device for your system and/or which device (i.e. soundcard) each of your applications will use to output their sound, etc.

You will need to set your outputs in *Sound Preferences* (*System -> Preferences -> Sound*) to *Autodetect*.

Having two soundcards does not mean that there will be a conflict. You just have to set one of them as the default.

You can easily have as many audio devices (soundcards, usb headsets, etc) as you want in your system. It does not matter.

I have tried disabling the onboard sound, but it hasn't made any difference (I should have mentioned that, but I'm pleased to have received a reply, and maybe you wouldn't have posted if I had!)

In any case, I am installing Pulse Audio Chooser ('apt-get install padevchooser'), and will let you know how I fare...

---

### Post by cov on 2008-11-11
Padevchooser just exits without an error.

---

### Post by cov on 2008-11-11
My machine has been locking up lately requiring to be turned off at the mains.

Today I noticed that when I powered down (<CNTRL><ALT><DEL>) the console locked up at "Stopping ALSA".

---

### Post by markbuntu on 2008-11-11
Try this, read the Sound Server setup and the Multiple Sound Cards sections and look in the link:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

