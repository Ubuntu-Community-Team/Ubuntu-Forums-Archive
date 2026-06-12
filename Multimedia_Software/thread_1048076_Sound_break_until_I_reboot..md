---
title: "Sound break until I reboot."
date: 2009-01-23
forum: Multimedia Software
---

### Post by alexandreracine on 2009-01-23
Hi all,

Just like that, I use sound, and then it does not work anymore. I do the same thing in Vista on the same machine (dual boot) and everything is fine. Either my sound just stop if I use flash games, quit the game and now want to use another application or the sound is repeating the last 1/10 of a second very fast. Yes, I can reboot and everything is fine, but I love trouble so I'll search if I can submit a bugreport if there is none about this. If there is one, please let me know.

**Some small stats...**

I currently use :
Ubuntu 8.10 - (Intrepid Ibex)
Rhythmbox that comes with it
Firefox with the normal flash player

**Possible causes**

Honestly, I don't know.
In my logs I have ...
Jan 22 01:21:37 ss pulseaudio[6045]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 22 19:44:58 ss pulseaudio[6045]: protocol-native.c: Failed to push data into queue
Jan 22 19:44:58 ss last message repeated 4355 times

Does this mean anything?

**More stats...**

```
sudo lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

```
sudo aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC883 Analog [ALC883 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC883 Digital [ALC883 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```


Let me know if anyone know something.

---

### Post by alexandreracine on 2009-01-28
Oh and looking in the system monitor, pulseaudio is in the futex_wait state.

---

### Post by alexandreracine on 2009-01-28
It is a bug! I'll follow up here [http://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093](http://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288093)

---

