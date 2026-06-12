---
title: "Previously working sound is broken, no clue as to why."
date: 2013-12-28
forum: Multimedia Software
---

### Post by Marvin666 on 2013-12-28
I'm running Xubuntu Quantal on the laptop shown in my signature. The gernal audio chipset is Intel. The machine also has an Nvidia chipset for HDMI audio, but I have no way of testing it's output.
Panel's mixer plugin is only showing a dummy output, and a monitor of it. I've not changed any setting or packages.
Speaker-test has no sound output, so I try to run alsamixer
```
cannot open mixer: No such file or directory
```
Next I tried: aplay -l
```
aplay: device_list:252: no soundcards found...
```
I forced an alsa reload, but that had no effect. Somebody on IRC that typically uses arch gave me a few commands to run, so here they are and the results. He seem stumped about them, but they may help you guys.
lsmod | grep snd_intel
```
snd_intel8x0           33107  0 
snd_ac97_codec        105652  1 snd_intel8x0
snd_pcm                80235  5 snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec
snd                    62146  12 snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
snd_page_alloc         14037  3 snd_hda_intel,snd_intel8x0,snd_pcm
```
sudo modprobe snd_intel8x0
```
(this command had no output)
```
lspci -v | grep -A7 -i "audio"
```
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Micro-Star International Co., Ltd. Device 1019
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```
Any help would be appreciated.

---

### Post by Marvin666 on 2013-12-30
Okay, so I'm using the old karmic xubuntu install on this sytem. Sound works fine on it, so it's not a hardware thing. I'll re-run the commands and paste their outputs here.
speaker-test ouputs sound just as it should.
alsamixer brings up a fully functional terminal mixer.
aplay -l returns:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lsmod | grep snd_intel
```
<no output>
```

sudo modprobe snd_intel8x0
```
<this again, does nothing>
```

lspci -v | grep -A7 -i "audio"
```
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Micro-Star International Co., Ltd. Device 1019
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

Instead out a dummy output, and a monitor of it, mixer's options are HDA Nvidia, and Nvidia MCP7A HDMI.
I hope this helps.

---

### Post by Yellow Pasque on 2013-12-31
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Marvin666 on 2014-01-03
[Results of Alsa Info.]("http://pastebin.com/cvkP08V1")

---

### Post by Yellow Pasque on 2014-01-04
Nasty error:
```
hda_codec: ALC888: SKU not ready 0x598301f0
```

Try latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Marvin666 on 2014-01-04
Thanks, that got it working again.

---

