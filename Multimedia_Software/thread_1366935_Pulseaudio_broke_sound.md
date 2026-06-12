---
title: "Pulseaudio broke sound"
date: 2009-12-29
forum: Multimedia Software
---

### Post by MooPi on 2009-12-29
I was using a terminal player "cplay for music and decided to upgrade to a graphical player "promoe" an xmms2 client. Had to install pulseaudio to get it to function. It worked until reboot. Now sound is broken. aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0Sound module
> Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 82bb
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by MooPi on 2009-12-29
Partial change in status. Sound can be enabled but is muted after reboot. What do I need to change to get pulseaudio unmuted on reboot. I've looked at the /etc/pulse config files and can't make sense of what I'm reading.

---

### Post by UDon on 2009-12-29
I'm a newbie that had all kinds of problems with Pulseaudio. I ended up uninstalling it in 9.04, and then added Gnome Alsamixer, which helped me to get sound going, though like yourself everything was muted whenever I rebooted. I upgraded to 9.10, but still had lots of problems as it also reinstalled Pulseaudio.

In the end I did a clean install of 9.10 last week, and this **seems** to have fixed my audio problems. I don't have an alsamixer anymore and just rely on Pulseaudio, but everything is working, from Skype to playing movies and Youtube clips.

If it is an option, I would recommend a clean install of 9.10 (after backing up critical files, of course!)

---

### Post by VertexPusher on 2009-12-29
> **MooPi said:**
> Had to install pulseaudio to get it to function.
No.

XMMS2 supports playback through ALSA, OSS, JACK, PulseAudio and libao. You can remove PulseAudio and configure XMMS2 to use ALSA.

---

### Post by MooPi on 2009-12-29
> **VertexPusher said:**
> No.

XMMS2 supports playback through ALSA, OSS, JACK, PulseAudio and libao. You can remove PulseAudio and configure XMMS2 to use ALSA.

Thank you VertexPusher, After looking into a howto on xmm2 I found the command to change output. ```
xmms2 config output.plugin alsa
```
Everything working as it should. Many Thanks.

---

