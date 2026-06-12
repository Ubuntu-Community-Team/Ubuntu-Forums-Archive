---
title: "no sound over HDMI"
date: 2022-10-28
forum: Multimedia Software
---

### Post by bjlockie on 2022-10-28
I installed lubuntu-22.10 on a new machine and I can't get the sound over the HDMI.
Should a driver for that device be listed?

```

$ inxi -SMA
System:
  Host: me-aspiretc281 Kernel: 5.19.0-23-generic arch: x86_64 bits: 64 Console: pty pts/0
    Distro: Ubuntu 22.10 (Kinetic Kudu)
Machine:
  Type: Desktop Mobo: Acer model: Aspire TC-281 serial: <superuser required>
    UEFI: American Megatrends v: R01-A2 date: 07/18/2017
Audio:
  Device-1: AMD Kabini HDMI/DP Audio driver: N/A
  Device-2: AMD Family 15h Audio driver: snd_hda_intel
  Sond Server-1: ALSA v: k5.19.0-23-generic running: yes
  Sound Server-2: PulseAudio v: 16.1 running: yes

```
I don't have an HDMI output device.


Works fine in lubuntu-22.04.1.

```
$ i$ inxi -SMA
System:
  Host: lubuntu Kernel: 5.15.0-43-generic x86_64 bits: 64
    Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Acer model: Aspire TC-281
    serial: <superuser required> UEFI: American Megatrends v: R01-A2
    date: 07/18/2017
Audio:
  Device-1: AMD Kabini HDMI/DP Audio driver: snd_hda_intel
  Device-2: AMD Family 15h Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-43-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

Drivers for both outputs and 3 sound servers.


Sond Server -1 typo in 22.10.

---

### Post by bjlockie on 2022-10-31
Vanilla kernel-6.1rc3 has the HDMI output. :-)

What kernel will 22.10 get to?

---

### Post by guiverc on 2022-11-01
Question has also been asked at [https://discourse.lubuntu.me/t/no-sound-over-hdmi/3718](https://discourse.lubuntu.me/t/no-sound-over-hdmi/3718)

Ubuntu 22.10 will have security fixes back-ported to it, just as per prior non-LTS releases.  There is no [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") option with non-LTS releases.

---

