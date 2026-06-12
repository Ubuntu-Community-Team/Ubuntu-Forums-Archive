---
title: "no sound on xubuntu 17.10"
date: 2018-04-10
forum: Multimedia Software
---

### Post by harlock593 on 2018-04-10
Hello,

i have no sound on an acer aspire 5315 sound card is intel hda realtek ALC268

aplay -l
> **** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: ALC268 Analog [ALC268 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0

lsmod> 
Module                  Size  Used by
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
ccm                    20480  6
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
coretemp               16384  0
arc4                   16384  2
snd_hda_codec_hdmi     49152  1
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
kvm                   593920  0
snd_hda_codec_realtek    98304  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hwdep              20480  1 snd_hda_codec
acer_wmi               20480  0
input_leds             16384  0
joydev                 20480  0
serio_raw              16384  0
snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
ath5k                 147456  0
sparse_keymap          16384  1 acer_wmi
ath                    28672  1 ath5k
mac80211              782336  1 ath5k
lpc_ich                24576  0
cfg80211              614400  3 mac80211,ath,ath5k
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  18 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
ene_ir                 20480  0
soundcore              16384  1 snd
rc_core                36864  1 ene_ir
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
mxm_wmi                16384  0
psmouse               147456  0
ahci                   36864  2
libahci                32768  1 ahci
pata_acpi              16384  0
i915                 1822720  4
tg3                   167936  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
video                  40960  2 acer_wmi,i915
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
wmi                    24576  2 acer_wmi,mxm_wmi
fb_sys_fops            16384  1 drm_kms_helper
ptp                    20480  1 tg3
drm                   360448  6 i915,drm_kms_helper
pps_core               20480  1 ptp

---

### Post by Yellow Pasque on 2018-04-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

