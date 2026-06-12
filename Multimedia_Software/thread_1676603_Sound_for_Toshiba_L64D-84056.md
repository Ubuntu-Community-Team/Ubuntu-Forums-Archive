---
title: "Sound for Toshiba L64D-84056"
date: 2011-01-27
forum: Multimedia Software
---

### Post by Tim-Tim on 2011-01-27
I can't for the life of me figure out how to enable sound on Ubuntu.  I have installed the latest version of ALSA and some (hopefully) useful output:

```
http://www.alsa-project.org/db/?f=dd516d9fab641ddff37e2622bf20a50a3694a792



lspci -v

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: Toshiba America Info Systems Device fdd0
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f4300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

aplay -l

** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Computer: Toshiba Satellite L645D-84056
```Any help would be appreciated.

---

### Post by gordintoronto on 2011-01-27
Do earphones work? While you were in Preferences/Sound, you checked that it's high volume and not muted?

---

### Post by Tim-Tim on 2011-01-27
Its not muted, and headphones do not work.  I have no sound at all, not even the system start up sound.

---

### Post by lidex on 2011-01-27
Try this using a Terminal="Applications->Accessories->Terminal" ```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

