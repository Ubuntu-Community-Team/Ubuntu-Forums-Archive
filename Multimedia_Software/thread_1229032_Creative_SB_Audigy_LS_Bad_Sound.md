---
title: "Creative SB Audigy LS Bad Sound"
date: 2009-08-01
forum: Multimedia Software
---

### Post by morowinger on 2009-08-01
Hi!
After installing my new Soundcard, the sound is working, but it sounds terrible. Here some informations:

the important section of **lsmod**
```

snd_ca0106             46368  3 
snd_ac97_codec        133848  1 snd_ca0106
snd_hda_intel         557492  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  4 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
rtl8187                54400  0 
snd_rawmidi            33920  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              251528  1 rtl8187
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           10624  1 rtl8187
snd                    78920  17 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfi_cmdset_0002        37248  1 
psmouse                64028  0 
ppdev                  16904  0 
soundcore              16800  1 snd
ac97_bus               10368  1 snd_ac97_codec
cfg80211               43680  2 rtl8187,mac80211
jedec_probe            22656  0 
fglrx                2376104  30 
serio_raw              14468  0 
snd_page_alloc         18704  3 snd_ca0106,snd_hda_intel,snd_pcm

```**lspci**
```

morowinger@morowinger-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
03:00.1 Audio device: ATI Technologies Inc HD48x0 audio

```**aplay -l**
```

morowinger@morowinger-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```has someone any hint how to get a better sound working?

---

### Post by kostkon on 2009-08-01
Try lowering the PCM volume level a little.

---

### Post by morowinger on 2009-08-01
seems to work, will check it now for some days and set it solved if it stays this good :)

thanks, enjoy this: :popcorn:

---

