---
title: "Logitech Quickcam issues"
date: 2009-09-14
forum: Multimedia Software
---

### Post by denham2010 on 2009-09-14
Hi,

I seem to be one of the many having problems with my Logitech USB QuickCam.

With a standard Ubuntu (Xubuntu) install, the camera worked with Camorama and with Flash in websites.

To get the cam working with aMSN, Skype and Cheese, I installed the latest gspca drivers from linuxtv.org

Fantastic, now Skype, aMSN and Cheese work.

Problem now is Camorama and Flash no longer akcnowledge the existence of the camera.

It's not such an issue with Camorama, as Cheese is the logical replacement for that. It's getting the camera to be recognised in Flash that I need.

Before updating the gspca drivers, flash asked me to choose between my TV card and the camera. Now it only shows the TV card.

Any ideas?

Output of lsmod
```
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             92200  0 
vboxdrv               121512  1 vboxnetflt
cx8800                 39632  0 
cx88xx                 85164  1 cx8800
ivtv                  151076  0 
cx2341x                22020  1 ivtv
bttv                  128660  0 
i2c_algo_bit           14084  3 cx88xx,ivtv,bttv
btcx_risc              13064  3 cx8800,cx88xx,bttv
lirc_i2c               17028  0 
lirc_dev               19892  1 lirc_i2c
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
tuner_simple           22800  1 
tuner_types            22912  1 tuner_simple
lp                     17156  0 
mt352                  14468  1 
saa7134_dvb            31372  11 
videobuf_dvb           15108  1 saa7134_dvb
dvb_core               95748  1 videobuf_dvb
saa7134_alsa           20512  0 
snd_hda_intel         434100  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
tda9887                18564  1 
snd_pcm                83076  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
tda8290                21000  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
tea5767                14852  1 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
tuner                  29960  2 
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gspca_stv06xx          32264  0 
joydev                 18496  0 
snd                    62756  15 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_pl                 11392  0 
saa7134               163148  3 saa7134_dvb,saa7134_alsa
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
nvidia               7233756  46 
gspca_main             31104  1 gspca_stv06xx
ppdev                  15620  0 
ff_memless             13320  1 hid_pl
psmouse                61972  0 
ir_common              51204  3 cx88xx,bttv,saa7134
intel_agp              34108  0 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
serio_raw              13444  0 
usbhid                 42336  1 hid_pl
v4l2_common            25472  7 cx8800,cx88xx,ivtv,cx2341x,bttv,tuner,saa7134
agpgart                42696  2 nvidia,intel_agp
pcspkr                 10496  0 
videobuf_dma_sg        20484  6 cx8800,cx88xx,bttv,saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          26244  6 cx8800,cx88xx,bttv,videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               20228  4 cx88xx,ivtv,bttv,saa7134
videodev               44192  9 cx8800,cx88xx,ivtv,bttv,tuner,saa7134,gspca_main,v4l2_common
v4l1_compat            21764  1 videodev
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Output from dmesg (it appears there is a problem with quickcam and the camera is now using STV06xx - the device registers as /dev/video1)
```
[    9.710490] quickcam: disagrees about version of symbol video_devdata
[    9.710494] quickcam: Unknown symbol video_devdata
[    9.710880] quickcam: disagrees about version of symbol video_unregister_device
[    9.710883] quickcam: Unknown symbol video_unregister_device
[    9.711070] quickcam: disagrees about version of symbol video_register_device
[    9.711073] quickcam: Unknown symbol video_register_device
[    9.846169] ppdev: user-space parallel port driver
[    9.857857] gspca: main v2.7.0 registered
......
[   10.315253] STV06xx: Probing for a stv06xx device
[   10.315257] gspca: probing 046d:0870
[   10.315261] STV06xx: Configuring camera
[   10.324258] STV06xx: HDCS-1020 sensor detected
[   10.324262] STV06xx: Initializing camera

```

lsusb
```
Bus 006 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```

v4l-info no longer shows the quickcam. Only the TV card.

Thanks.

---

### Post by viktara on 2009-09-14
Hi,

Which version of flash are you using?

Flash 10 has better support for webcams.

Also check out flashcam:
[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

That might help.


Regards



Vik

---

### Post by denham2010 on 2009-09-16
Thanks for your help.

Unfortunately vloopback fails on my system. The module fails with:

```
FATAL: Error inserting vloopback (/lib/modules/2.6.28-15-generic/kernel/drivers/misc/vloopback.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Flashcam is installed. It's just vloopback.

Googling the error tells me I need the module videodev installed.

Result of lsmod | grep videodev

```
videodev               44192  8 cx8800,cx88xx,ivtv,bttv,tuner,gspca_main,saa7134,v4l2_common
v4l1_compat            21764  1 videodev

```

So videodev is there.

I have tried compiling vloopback from svn and from the tar.gz for kernel 2.6.28 and both still fail with the same error.

Output in dmesg

```
[ 3240.246271] vloopback: disagrees about version of symbol video_devdata
[ 3240.246276] vloopback: Unknown symbol video_devdata
[ 3240.246425] vloopback: disagrees about version of symbol video_unregister_device
[ 3240.246427] vloopback: Unknown symbol video_unregister_device
[ 3240.246528] vloopback: disagrees about version of symbol video_device_alloc
[ 3240.246530] vloopback: Unknown symbol video_device_alloc
[ 3240.246638] vloopback: disagrees about version of symbol video_register_device
[ 3240.246641] vloopback: Unknown symbol video_register_device
[ 3240.246785] vloopback: disagrees about version of symbol video_device_release
[ 3240.246787] vloopback: Unknown symbol video_device_release
[ 3390.407342] vloopback: disagrees about version of symbol video_devdata
[ 3390.407347] vloopback: Unknown symbol video_devdata
[ 3390.407494] vloopback: disagrees about version of symbol video_unregister_device
[ 3390.407497] vloopback: Unknown symbol video_unregister_device
[ 3390.407597] vloopback: disagrees about version of symbol video_device_alloc
[ 3390.407600] vloopback: Unknown symbol video_device_alloc
[ 3390.407707] vloopback: disagrees about version of symbol video_register_device
[ 3390.407709] vloopback: Unknown symbol video_register_device
[ 3390.407854] vloopback: disagrees about version of symbol video_device_release
[ 3390.407856] vloopback: Unknown symbol video_device_release
[ 3982.442330] vloopback: disagrees about version of symbol video_devdata
[ 3982.442335] vloopback: Unknown symbol video_devdata
[ 3982.442482] vloopback: disagrees about version of symbol video_unregister_device
[ 3982.442485] vloopback: Unknown symbol video_unregister_device
[ 3982.442584] vloopback: disagrees about version of symbol video_device_alloc
[ 3982.442587] vloopback: Unknown symbol video_device_alloc
[ 3982.442693] vloopback: disagrees about version of symbol video_register_device
[ 3982.442696] vloopback: Unknown symbol video_register_device
[ 3982.442840] vloopback: disagrees about version of symbol video_device_release
[ 3982.442843] vloopback: Unknown symbol video_device_release

```

Any ideas?

---

