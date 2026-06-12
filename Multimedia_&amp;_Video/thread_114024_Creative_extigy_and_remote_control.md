---
title: "Creative extigy and remote control"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by juuva on 2006-01-07
Ubuntu 5.10 with kernel: 2.6.12-10-386 #1 found extigy when I plugget it on, but remote control doesn't work.

Light on extigy flashes but nothing happens. Also after unplugging/turning extigy off linux doesn't seam to find extigy before restart. When computer is not powered on, remote control works, so it seams that controlling volume etc. must be done via os. when it is operational.

I tried to install lirc but couldn't find/compile kernel modules for it. Any suggestions?

loaded usb-modules:
```

$ cat /proc/modules |grep usb
snd_usb_audio 68160 1 - Live 0xdfc74000
snd_usb_lib 13824 1 snd_usb_audio, Live 0xdfc6f000
snd_rawmidi 22816 1 snd_usb_lib, Live 0xdfbd6000
snd_hwdep 8608 1 snd_usb_audio, Live 0xdfc61000
snd_pcm 78344 5 snd_usb_audio,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xdfb99000
snd 48644 13 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xdfae3000
usbcore 104316 5 snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd, Live 0xdf91e000

```

---

### Post by juuva on 2006-01-07
sndstat just for case..
```

$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux k10 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel ICH5 with AD1985 at 0xffa7f800, irq 17
Brooktree Bt878 at 0xe6aff000, irq 21
Creative Technology Ltd. Sound Blaster Extigy at usb-0000:00:1d.0-1, full speed

Audio devices:
0: Intel ICH5 (DUPLEX)
1: Bt87x Digital
2: USB Audio (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
2: Sound Blaster Extigy

Timers:
7: system timer

Mixers:
0: Analog Devices AD1985
1: Bt87x
2: USB Mixer

```

---

