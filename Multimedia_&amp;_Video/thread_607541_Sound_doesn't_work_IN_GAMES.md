---
title: "Sound doesn't work IN GAMES"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by bobbyj99 on 2007-11-09
I am having sound issues. Sound is working fine for everything except system sounds and in games (World of Padman, Wormux, and Second Life just to name a few). Other audio works just fine (music, Skype, Pidgin, etc.). Here are the outputs from lsmod and aplay -l.

```
robert@TUX:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  3 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  16 
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
lp                     12580  0 
saa7134_alsa           15392  0 
sg                     36764  0 
sd_mod                 30336  0 
nvidia               6221648  24 
agpgart                35016  1 nvidia
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
k8temp                  6656  0 
analog                 13344  0 
gameport               16776  1 analog
snd_intel8x0           34972  2 
snd_ac97_codec        100644  1 snd_intel8x0
psmouse                39952  0 
tuner                  63144  0 
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
pcspkr                  4224  0 
serio_raw               8068  0 
saa7134               129100  1 saa7134_alsa
video_buf              26244  2 saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
gspca                 608336  0 
videodev               29312  2 saa7134,gspca
v4l2_common            18432  3 tuner,saa7134,videodev
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_usb_audio          81024  2 
v4l1_compat            15364  2 saa7134,videodev
snd_pcm                80388  7 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_usb_lib            17920  1 snd_usb_audio
xpad                    9988  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_hwdep              10244  1 snd_usb_audio
snd_rawmidi            25728  3 snd_mpu401_uart,snd_seq_midi,snd_usb_lib
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  20 saa7134_alsa,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_nforce2             7040  0 
i2c_core               26112  5 nvidia,tuner,saa7134,ir_kbd_i2c,i2c_nforce2
joydev                 11328  0 
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  3 
cdrom                  37536  1 ide_cd
ide_disk               18560  9 
usb_storage            73024  0 
libusual               18448  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,amd74xx
sata_nv                20612  0 
floppy                 60004  0 
forcedeth              51592  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  10 gspca,snd_usb_audio,snd_usb_lib,xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  9 
apparmor               40728  0 
commoncap               8320  1 apparmor
``````
robert@TUX:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Any other info you need to assist me...just ask.

Thanks in advance :D

---

### Post by bobbyj99 on 2007-11-09
OK, I don't know what happened. Today when I turned on my computer everything works fine. This has happened before. Does anybody know why or what I can do to stop it from happening again? 

It's playing with my emotions and I don't know how much more I can take...:lolflag:

Thanks again...

---

