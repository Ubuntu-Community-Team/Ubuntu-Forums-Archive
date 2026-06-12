---
title: "Ubuntu 10.04 mic not working (9.10 was okey)"
date: 2010-06-19
forum: Multimedia Software
---

### Post by hphd-Blokkolnam on 2010-06-19
Hello,

A few days ago I have installed Ubuntu 10.04 on my desktop PC (i had 9.10 before since its release). Everything is just working, except one annoying thing: i cannot get the microphone work :( I have searched several days the net, but cannot solve so far the problem. Tried sound recorder, Skype, but nothing.
Maybe It is important to mention, that I have a TV-tuner card, and it works fine, the tuner output is hooked into the line-in on my motherboard (and sound is okey). 

I was playing with several things trying to solve the problem:

1., 
alsamixergui, gnome-alsa-mixer many different settings...

2., 
I can only see in Skype sound devices settings: "PulseAudio server (local)". In Ubuntu 9.10 I was able to change to different "ports". I followed this guide to "open" up the options: 
[http://ubuntuforums.org/showthread.php?t=1490687](http://ubuntuforums.org/showthread.php?t=1490687)
> When I went to ~/.pulse and created the file client.conf, opening it and  adding the line "autospawn =no" (Without quotes of course), the next  time I ran the program, any audio program really, I suddenly had access  to all of the inputs and outputs of both my sound cards.Unfortunately, even if i tried every options in Skype to set the mic, no goal so far :(

3., 
I tried to modify my etc/modprobe.d/alsa-base.conf , to put these in the end of the file:
```
options snd-hda-intel model=snd-via82xx
options snd-hda-intel probe_mask=1
```Did not solve the mic problem either :(


Here some info about my config:

```
cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9761A+ at 0xe400, irq 22

```lsmod:
```
andras@andras-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ir_kbd_i2c              5431  0 
tda827x                 9240  1 
arc4                    1153  2 
snd_via82xx            20871  3 
tda8290                12092  1 
gameport                9089  1 snd_via82xx
snd_ac97_codec        101347  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
tuner                  20412  1 
snd_pcm_oss            41611  0 
snd_mixer_oss          13461  2 snd_pcm_oss
snd_pcm                78086  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7140  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6001  1 snd_via82xx
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
snd_seq_dummy           1498  0 
snd_seq_oss            30866  0 
snd_seq_midi            5101  0 
snd_rawmidi            19879  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      5939  2 snd_seq_oss,snd_seq_midi
snd_seq                51494  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
saa7134               143391  1 
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
snd_timer              19106  2 snd_pcm,snd_seq
snd_seq_device          5990  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
ir_common              38875  2 ir_kbd_i2c,saa7134
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
mac80211              204922  2 rt2x00usb,rt2x00lib
nvidia               9932176  38 
ppdev                   5259  0 
v4l2_common            15431  2 tuner,saa7134
snd                    62362  18 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
vgastate                8961  1 vga16fb
cfg80211              126485  2 rt2x00lib,mac80211
videodev               34361  4 tuner,saa7134,v4l2_common
v4l1_compat            13251  1 videodev
videobuf_dma_sg        10782  1 saa7134
psmouse                63245  0 
serio_raw               3978  0 
i2c_viapro              5573  0 
soundcore               6620  2 snd
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
shpchp                 28820  0 
via_agp                 5310  1 
parport_pc             25962  1 
agpgart                31724  2 nvidia,via_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
via_rhine              19154  0 
mii                     4381  1 via_rhine
pata_via                7272  0 
sata_via                6945  2 
floppy                 53016  0 

```my /etc/modprobe.d/alsa-base.conf:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=snd-via82xx
options snd-hda-intel probe_mask=1
```

And some more:
```
uname -a
Linux andras-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

```

```
dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                   0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  linux-alsa-driver-modules-2.6.32-22-generic    2.6.32-22.201005210601                          Ubuntu-supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.

```


Someone could give me some help?
Thanks in advance!
Regards to the community

---

### Post by trion1 on 2010-06-26
mine working with putting "position_fix=1" after model and it should work for internal and external mic:
options snd-hda-intel model=snd-via82xx position_fix=1

---

### Post by hphd-Blokkolnam on 2010-06-26
thanks for the info, maybe later I will give it a try. Actually I did a downgrade back to 9.10, because for me the 10.04 seems to be "buggy". Just a few things: the mentioned microphone problem, very strange problem with my TV-tuner card (MSI TV@Anywhere Plus, channels not working under 250MHz), automount not working, etc...

With 9.10 everything is just working...maybe I have to wait a few months, until proper patches will appear for the 10.04 release.....

---

### Post by lidex on 2010-06-26
That is not an hda-intel codec, so your alsa-base options are not going to work. For position fix the correct widget option would be:
```
options snd-via82xx position_fix=1 
```

---

