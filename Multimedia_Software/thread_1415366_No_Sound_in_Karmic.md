---
title: "No Sound in Karmic"
date: 2010-02-24
forum: Multimedia Software
---

### Post by Zzebodiah on 2010-02-24
I'm sure I'm missing something obvious but I can't seem to figure out what. I have only just got Ubuntu and my first was 9.10 and my speakers are outputting nothing, it worked on my previous xp but not this. I checked hardware drivers but nothing missed there.
I ran "lspci" to see what audio device I had and got two results;

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

00:0d.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)

this left me a bit confused as to where i should go from here. I searched around but couldn't see anything that I understood or that worked.

thought this might be useful: "sudo lsmod"
Module                  Size  Used by
snd_usb_audio          84224  1 
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  1 snd_usb_audio
gspca_pac7311           9788  0 
gspca_main             22812  1 gspca_pac7311
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
snd_atiixp_modem       11940  0 
snd_via82xx_modem      11204  0 
snd_intel8x0m          13896  0 
snd_ens1371            22016  2 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  3 
iptable_filter          3100  0 
gameport               11368  1 snd_ens1371
snd_ac97_codec        101216  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_seq_dummy           2656  0 
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
joydev                 10240  0 
serio_raw               5280  0 
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  9 snd_usb_audio,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
nvidia               9586440  36 
parport_pc             31940  1 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_usb_lib,snd_ens1371,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  27 snd_usb_audio,snd_hwdep,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
shpchp                 32272  0 
i2c_sis96x              3904  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
hid_logitech            8412  0 
ff_memless              5188  1 hid_logitech
usbhid                 38208  1 hid_logitech
usb_storage            52576  1 
ssb                    35364  1 b43
sis900                 19932  0 
mii                     5212  1 sis900
floppy                 54916  0 
sis_agp                 6972  1 
agpgart                34988  2 nvidia,sis_agp

but unfortunately it's all gibberish to me. Any help would be gratefully appreciated.
cheers

EDIT: Got frustrated and gave my speaker a good slap, started working >.< oh well beggars can't be choosers and all.

---

