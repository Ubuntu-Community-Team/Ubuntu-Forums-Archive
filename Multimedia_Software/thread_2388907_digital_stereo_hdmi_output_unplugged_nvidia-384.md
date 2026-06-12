---
title: "digital stereo hdmi output unplugged nvidia-384"
date: 2018-04-09
forum: Multimedia Software
---

### Post by lance bermudez on 2018-04-09
I can get the display to work but not the sound.

[ATTACH=CONFIG]279219[/ATTACH][ATTACH=CONFIG]279220[/ATTACH][ATTACH=CONFIG]279221[/ATTACH][ATTACH=CONFIG]279222[/ATTACH]

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"

Additional Drivers
NVIDIA Corpation: Unknown
Using Nvidia Binary driver -version 384.111 from nvidia-384(proprietary, tested)

~$ aptitude search pavucontrol
i   pavucontrol                     - PulseAudio Volume Control                 
p   pavucontrol:i386                - PulseAudio Volume Control                 
i   pavucontrol-dbg                 - Debugging symbols for pavucontrol         
p   pavucontrol-dbg:i386            - Debugging symbols for pavucontrol

---

### Post by Autodave on 2018-04-09
Where did you get the Nvidia driver from?

Have you tried another HDMI cable? Cables do fail and older HDMI cables do not transmit audio.

---

### Post by lance bermudez on 2018-04-10
in ubuntu the program synaptic that has the Additional Drivers part so I think that is comes from nvidia.

---

### Post by lance bermudez on 2018-04-11
$ sudo lshw -c sound
```

  *-multimedia
       description: Audio device
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:133 memory:b4428000-b442bfff memory:b4410000-b441ffff

```

lspci -v | grep -i audio
```

00:1f.3 Audio device: Intel Corporation Device a171 (rev 31)

```

$ aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

$ lsmod | grep intel
```

btintel                16384  1 btusb
bluetooth             548864  26 btrtl,btintel,bnep,btbcm,btusb
intel_rapl             20480  0
intel_powerclamp       16384  0
kvm_intel             204800  0
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm                   589824  1 kvm_intel
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
intel_cstate           20480  0
intel_rapl_perf        16384  0
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
ghash_clmulni_intel    16384  0
aesni_intel           188416  8
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel,aesni_intel
pinctrl_intel          20480  1 pinctrl_sunrisepoint

```

$ lsmod | grep snd
```

snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    98304  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd

```

---

