---
title: "Sound gone poof"
date: 2009-08-22
forum: Multimedia Software
---

### Post by Noccy on 2009-08-22
Was watching a video in Miro yesterday. Was fiddling with my friends phone that was being upgraded as well, so had my back to the PC when we both suddenly realized the sound was gone. I tried the sound test, exaile, miro, and none of them rendered anything but crackling.

Went on to test the different drivers. ESD and OSS works, while Alsa and Pulseaudio doesn't.

I tried reinstalling the pulse and gstreamer packages to no avail. I tried compiling and installing them from source, still no go.

```
[   12.067958] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.068097] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.101942] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.102767] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   12.102779] HDA Intel: probe of 0000:00:1b.0 failed with error -22
```

```
noccy@aurora:/etc$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
```

```
noccy@aurora:/etc$ lsmod | grep -i snd
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
```

Edit: Still no sound, added a few more lines from dmesg. Have asked in #alsa, reinstalled alsa, gstreamer, and tons of stuff. Tried aplay, which appears to function through pulse and produces output. Checked pavucontrol, the devices are listed. However, I don't have any sound devices available in Gnome any more and the mixer throws me an error about missing GStreamer plugins/devices for volume control.

---

