---
title: "Default desktop 13.10 install and no sound"
date: 2013-12-26
forum: Multimedia Software
---

### Post by Castlef on 2013-12-26
I have a music streamer II hooked up to USB and it goes to a splitter which goes to a cambridge audio amp and also a headphone amp. On windows I get sound just fine but no sound on here. My motherboard is an x58 asus sabertooth.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: II [Music Streamer II], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia_2 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia_2 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia_2 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia_2 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
 lsmod
Module                  Size  Used by
ftdi_sio               49105  1 
usbserial              44667  3 ftdi_sio
snd_hda_codec_hdmi     41276  12 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
nvidia              11309674  94 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mxm_wmi                13021  0 
ext2                   72832  1 
joydev                 17377  0 
snd_usb_audio         149162  2 
snd_usbmidi_lib        25070  1 snd_usb_audio
snd_hda_codec_realtek    51465  1 
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
lpc_ich                21080  0 
snd_hda_intel          48171  9 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102033  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i7core_edac            24122  0 
edac_core              62312  1 i7core_edac
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  35 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
asus_atk0110           18657  0 
mac_hid                13205  0 
wmi                    19070  1 mxm_wmi
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
pata_acpi              13038  0 
firewire_ohci          40060  0 
firewire_core          64476  1 firewire_ohci
r8169                  67341  0 
crc_itu_t              12707  1 firewire_core
mii                    13934  1 r8169
ahci                   25819  2 
libahci                31898  1 ahci

```

---

