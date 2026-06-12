---
title: "No sound for Acer Aspire M3202 desktop computer on kubuntu 8.04"
date: 2009-09-04
forum: Multimedia Software
---

### Post by tsanchung on 2009-09-04
No sound for Acer Aspire M3202 desktop computer on 32-bit kubuntu 8.04
when playing a CD with Amarok or "speaker-test -c2 -twav".
However, sound is working for the same computer playing the same CD on 32-bit ubuntu 9.04, so hw is not the issue.
Acer does not support linux so they do not answer my question.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

$ lspci -v
...
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
Subsystem: Acer Incorporated [ALI] Unknown device 014e
Flags: bus master, slow devsel, latency 64, IRQ 20
Memory at fe7f4000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

...
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
Subsystem: ATI Technologies Inc RS780 Azalia controller
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at fe9e8000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

# cat /proc/asound/cards
0 [SB ]: HDA-Intel - HDA ATI SB
HDA ATI SB at 0xfe7f4000 irq 20
1 [HDMI ]: HDA-Intel - HDA ATI HDMI
HDA ATI HDMI at 0xfe9e8000 irq 19

# modprobe snd_hda_intel

...
I modified alsa-base from 8.04.
$ sudo gvim /etc/modprobe.d/alsa-base
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel

#options snd-hda-intel model=acer
#options snd-hda-intel model=acer-aspire
options snd-hda-intel model=auto

options snd slots=snd-hda-intel,snd-hda-intel
#options snd-hda-intel enable_msi=1 probe_mask=1
options snd-hda-intel probe_mask=1


I copied alsa-base.conf from ubuntu 9.04
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

...
dmesg:
[ 234.407317] hda-intel: Invalid position buffer, using LPIB read
method instead.

I had used alsamixer to set the volume to a reasonable value.

Graphics hw is ATI Radeon HD 3200.
CPU is AMD Phenom 8550 Triple-Core Processor.

Please help to fix the audio problem.
Thanks.

---

