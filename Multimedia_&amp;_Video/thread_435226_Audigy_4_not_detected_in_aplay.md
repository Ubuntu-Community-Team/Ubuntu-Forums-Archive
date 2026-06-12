---
title: "Audigy 4 not detected in aplay"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Cappy on 2007-05-06
My Audigy 4 was working but it just suddenly stopped. I tried taking it out, plugging it in. Nothing changes.

$lspci line:
01:0a.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Just shows my onboard sound

dmesg error:
[   32.297895] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   32.417251] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   32.647273] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   32.775367] cannot find the slot for index 0 (range 0-0)
[   32.775411] EMU10K1_Audigy: probe of 0000:01:0a.0 failed with error -12
[   32.941691] fuse init (API version 7.8)

Edit:
I solved this 1 minute after I posted it.
I removed the line "options snd-emu10k1 index=0" from a file I had made in /etc/modprobe.d which I put there because my sound card would sometimes not be device "0" when I booted up. Removing it seems to fix it. Weird.

---

