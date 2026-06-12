---
title: "sound problem"
date: 2013-12-24
forum: Multimedia Software
---

### Post by olravmik on 2013-12-24
Hi Im relativly new to ubuntu. Heving sound problem:

/sbin/alsa: Warning: Processes using sound devices: 10804(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-usb-audio snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-usb-audio snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-usb-audio snd-pcm snd-hwdep snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc.

what to do? Sound is muted end unmuted.

---

### Post by tgalati4 on 2013-12-24
Open a terminal, post the output of:

```
aplay -l
```  That's a lower-case "L".

Also post the following:

```
lsmod
```

What version of Ubuntu are you using and what exactly are you doing to cause this issue?

---

### Post by olravmik on 2013-12-26
guest-vSWqCv@oleg-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by olravmik on 2013-12-26
guest-vSWqCv@oleg-desktop:~$ lsmod
Module                  Size  Used by
rfcomm                 38400  0 
bnep                   17852  2 
bluetooth             211552  10 rfcomm,bnep
parport_pc             27612  0 
ppdev                  12849  0 
ext2                   63952  1 
snd_hda_codec_hdmi     36612  4 
nvidia               8503151  90 
snd_hda_codec_realtek    65042  1 
snd_hda_intel          38819  10 
snd_hda_codec         118650  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         116657  2 
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
uvcvideo               72250  0 
videobuf2_core         39385  1 uvcvideo
kvm_amd                54759  0 
snd_pcm                85934  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
kvm                   384557  1 kvm_amd
videodev               96131  2 uvcvideo,videobuf2_core
snd_usbmidi_lib        24589  1 snd_usb_audio
videobuf2_vmalloc      12920  1 uvcvideo
aesni_intel            18196  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_seq_midi           13132  0 
ablk_helper            13357  1 aesni_intel
snd_rawmidi            25157  2 snd_usbmidi_lib,snd_seq_midi
cryptd                 19821  1 ablk_helper
snd_seq_midi_event     14475  1 snd_seq_midi
lrw                    13127  1 aesni_intel
aes_i586               16995  1 aesni_intel
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
xts                    12778  1 aesni_intel
gf128mul               14503  2 lrw,xts
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  35 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
k10temp                12997  0 
fam15h_power           12998  0 
drm                   233935  3 nvidia
psmouse                82769  0 
sp5100_tco             13558  0 
eeepc_wmi              12983  0 
asus_wmi               23821  1 eeepc_wmi
serio_raw              13031  0 
sparse_keymap          13658  1 asus_wmi
microcode              18433  0 
video                  19116  1 asus_wmi
i2c_piix4              13227  0 
mxm_wmi                12893  0 
ati_agp                13242  0 
wmi                    18744  2 asus_wmi,mxm_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0 
usbhid                 46125  0 
usb_storage            48053  0 
hid                    87362  2 hid_generic,usbhid
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   25631  5 
r8169                  62532  0 
libahci                26336  1 ahci

---

### Post by olravmik on 2013-12-26
I have Ubuntu 12.04.3 installed but the same problem was with  13.10.

---

### Post by tgalati4 on 2013-12-26
You have two sets of sound hardware on your machine--on-board motherboard sound chip, which looks like an Intel HDA chip which supports both analog and digital sound.  Then you have an nVidia card with HDMI sound.  Try turning off one of them in BIOS and see if that fixes the problem.  You have two sets of sound drivers loaded and ALSA is getting confused.

What kind of computer is this?  What sound hardware do you have?  Which sound are your trying to get to work?

---

### Post by Yellow Pasque on 2013-12-27
Please describe problem in greater detail and give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) 
Your first post doesn't show any issue other than a warning that pulseaudio is using the sound device, which is expected.

> You have two sets of sound hardware on your machine--on-board motherboard sound chip, which looks like an Intel HDA chip which supports both analog and digital sound. Then you have an nVidia card with HDMI sound. Try turning off one of them in BIOS and see if that fixes the problem. You have two sets of sound drivers loaded and ALSA is getting confused.

Onboard sound and HDMI sound will coexist peacefully. There is no need to disable anything in the BIOS as long as user selects the intended output in the sound control.

---

### Post by olravmik on 2013-12-27
[http://www.alsa-project.org/db/?f=157c7cdd1eb33bc0030207f0dedfb8f4525b5032](http://www.alsa-project.org/db/?f=157c7cdd1eb33bc0030207f0dedfb8f4525b5032)

---

### Post by Yellow Pasque on 2013-12-27
> **olravmik said:**
> [http://www.alsa-project.org/db/?f=157c7cdd1eb33bc0030207f0dedfb8f4525b5032](http://www.alsa-project.org/db/?f=157c7cdd1eb33bc0030207f0dedfb8f4525b5032)

What is the issue? No sound?

---

### Post by olravmik on 2013-12-27
Sound is playing but it continiously swiching between analog stereo autput end headphones, sometimes it muts sound

---

### Post by olravmik on 2013-12-27
sometimes it continiously mutes sound and i cant do anithing to unmute

---

### Post by Yellow Pasque on 2013-12-28
> Sound is playing but it continiously swiching between analog stereo autput end headphones, sometimes it muts sound 

In that case, I would make a log capturing the behavior and file a bug: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

