---
title: "Sound borked locally, not over airtunes.."
date: 2011-09-08
forum: Multimedia Software
---

### Post by vertigo420 on 2011-09-08
Hey guys,

So I was trying to get Quake 2 running natively on Linux, and finally got the OpenGL renderer working well enough that I then wanted sound. Until then, all sound worked just fine on my box, including over Airtunes via the pulseaudio raop module.

Ill admit, I was stabbing at the problem with rusty nails, and cant quite remember what I installed now, but there was some mucking about with alsa oss packages which may have done the damage, but for whatever reason, my sound no longer functioned - at all. During some troubleshooting, I noted that the hardware was being detected fine, but no driver module was being loaded for it.

```
modprobe snd_hda_intel
```... addressed that, and I could even select the sound output! But nothing I played would actually come through my headphones, even tho nothing was muted, but I can select the Airtunes sound sink and stream to that just fine.

???

My local output is borked but the remote one is fine?

lspci -v
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 840b
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```lshw -C multimedia
```

  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:f9ffc000-f9ffffff

```Everything seems to be in order! What Is wrong!? :confused:

One more thing... Ill try parsing my bash history and removing exactly the packages that were installed. Looks like they were oss4-base and oss4-dev. Will reboot after posting this.

---

### Post by vertigo420 on 2011-09-08
Ok, seems at some point during reinstalling packages, volume was muted after all. :lolflag: What a fool. Oh well, working fine now.

---

