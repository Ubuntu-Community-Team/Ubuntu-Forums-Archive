---
title: "A no-longer-working DVB-T card"
date: 2009-07-02
forum: Multimedia Software
---

### Post by bgbnbigben on 2009-07-02
Hey All,

So as late as tuesday, Kaffeine was able to pick up my VideoMate DVB-T card, and was able to record programs without a hitch.
Today, however, when i went to run Kaffeine, i was stumped to see no little icon saying "Digital TV", which the help pages promise should show up if i have a TV card correctly installed.
Making sure this wasnt just a Kaffeine error, i jammed the "w_scan -c AU -x initial-tuning-data.txt" command into terminal, and sure enough, this output occured
```
main:2877: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
```I tried re-installing video4linux's items, i tried re-installing kaffeine and i've tried modprobing saa7134 (the module needed for my type of tv card, which has the following modules loaded:
```
ben@Ben-Ubuntu:~$ lsmod |grep saa7134
saa7134_alsa           20000  0 
snd_pcm                82948  4 snd_hda_intel,saa7134_alsa,snd_pcm_oss
saa7134               152020  1 saa7134_alsa
ir_common              52228  1 saa7134
videodev               41600  1 saa7134
compat_ioctl32          9344  1 saa7134
v4l2_common            20992  1 saa7134
videobuf_dma_sg        20484  2 saa7134_alsa,saa7134
videobuf_core          26500  2 saa7134,videobuf_dma_sg
tveeprom               20100  1 saa7134
snd                    62628  19 snd_hda_intel,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```Can anyone provide any help on the matter?
ben

---

### Post by bgbnbigben on 2009-07-04
Shameless self bump.

C'mon, surely someone must know how to fix this / be able to offer some advice on my problem!

---

### Post by mtron on 2009-07-04
have a look at your dmesg output. (post "dmesg | grep -i dvb") maybe soething went wrong with the driver install / kernel update.

---

### Post by Jose Catre-Vandis on 2009-07-04
Can't see the "saa7134_dvb" module in your lsmod. Try modprobing that?

Don't have the same model but do have the same module requirements.Here is my lsmod output for saa7134 if it helps (on xubuntu 9.04, don't use kaffiene!)

```
saa7134_dvb            28556  0 
videobuf_dvb           15236  1 saa7134_dvb
saa7134_alsa           20000  0 
dvb_core               92032  2 saa7134_dvb,videobuf_dvb
snd_pcm                82948  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
saa7134               152020  2 saa7134_dvb,saa7134_alsa
ir_common              52228  1 saa7134
videodev               41600  2 tuner,saa7134
compat_ioctl32          9344  1 saa7134
v4l2_common            20992  2 tuner,saa7134
videobuf_dma_sg        20484  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          26500  3 videobuf_dvb,saa7134,videobuf_dma_sg
snd                    62628  13 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               20100  1 saa7134
```

---

### Post by bgbnbigben on 2009-07-04
yup, that modprobe did it. cheers :)
ill stick that into my /etc/modules so i dont have to worry about it every time i boot up
now to watch the footy!

---

### Post by Jose Catre-Vandis on 2009-07-04
:)

---

