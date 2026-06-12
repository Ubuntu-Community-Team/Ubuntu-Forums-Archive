---
title: "Ralink Wireless woes (RT2870)"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by echorequest on 2010-01-24
Hello,

Iam trying to get my Zonet ZEW2500P usb going. I installed the windows .inf file off  the CD.
some output:

da@da-ASUS:~$ lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

da@da-ASUS:~$ ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt2870 : driver installed
    device (148F:3070) present (alternate driver: rt2800usb)

da@da-ASUS:~$ iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.

da@da-ASUS:~$ lsmod

Module                  Size  Used by
ndiswrapper           185692  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_bt87x              12708  1 
snd_hda_intel          26984  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75520  4 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss
tda18271               35556  1 
lgdt3305               12256  1 
snd_seq_dummy           2656  0 
tuner_simple           14832  1 
tuner_types            14396  1 tuner_simple
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110            8252  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
tuner                  21540  1 
tvaudio                25884  0 
tda7432                 5016  0 
msp3400                28204  0 
bttv                  119412  0 
ir_common              48512  1 bttv
i2c_algo_bit            5760  1 bttv
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
cx23885               100444  0 
cx2341x                13440  1 cx23885
videobuf_dma_sg        12608  2 bttv,cx23885
v4l2_common            17500  7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,cx2341x
videodev               36736  7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,v4l2_common
v4l1_compat            14496  1 videodev
videobuf_dvb            7040  1 cx23885
dvb_core               87364  3 lgdt3305,cx23885,videobuf_dvb
videobuf_core          17952  4 bttv,cx23885,videobuf_dma_sg,videobuf_dvb
btcx_risc               4772  2 bttv,cx23885
tveeprom               11872  2 bttv,cx23885
snd                    59204  19 snd_hda_codec_realtek,snd_bt87x,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                1989980  34 
soundcore               7264  1 snd
snd_page_alloc          9252  3 snd_bt87x,snd_hda_intel,snd_pcm
floppy                 54980  0 
usbhid                 38304  0 
atl1e                  31888  0 
intel_agp              27748  0 
agpgart                35020  2 fglrx,intel_agp
da@da-ASUS:~$ lsmod
Module                  Size  Used by
ndiswrapper           185692  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_bt87x              12708  1 
snd_hda_intel          26984  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75520  4 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss
tda18271               35556  1 
lgdt3305               12256  1 
snd_seq_dummy           2656  0 
tuner_simple           14832  1 
tuner_types            14396  1 tuner_simple
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110            8252  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
tuner                  21540  1 
tvaudio                25884  0 
tda7432                 5016  0 
msp3400                28204  0 
bttv                  119412  0 
ir_common              48512  1 bttv
i2c_algo_bit            5760  1 bttv
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
cx23885               100444  0 
cx2341x                13440  1 cx23885
videobuf_dma_sg        12608  2 bttv,cx23885
v4l2_common            17500  7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,cx2341x
videodev               36736  7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,v4l2_common
v4l1_compat            14496  1 videodev
videobuf_dvb            7040  1 cx23885
dvb_core               87364  3 lgdt3305,cx23885,videobuf_dvb
videobuf_core          17952  4 bttv,cx23885,videobuf_dma_sg,videobuf_dvb
btcx_risc               4772  2 bttv,cx23885
tveeprom               11872  2 bttv,cx23885
snd                    59204  19 snd_hda_codec_realtek,snd_bt87x,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                1989980  34 
soundcore               7264  1 snd
snd_page_alloc          9252  3 snd_bt87x,snd_hda_intel,snd_pcm
floppy                 54980  0 
usbhid                 38304  0 
atl1e                  31888  0 
intel_agp              27748  0 
agpgart                35020  2 fglrx,intel_agp
da@da-ASUS:~$ 

When i use the wireless network drivers gui (ndisgtk)
 it shows the rt2870 driver and that the hardware is present.
clicking on the configure network button i get a message: "could not find a network configuration tool"

Any suggestions to try would be appreciated.

---

### Post by pdc on 2010-01-24
you're trying to use ndiswrapper and the windows driver;

have a read at the final post here;

[http://ubuntuforums.org/showthread.php?t=1289917&page=2](http://ubuntuforums.org/showthread.php?t=1289917&page=2)

the person posting seemed also to need the rt2870 and their system seemed to configure up fine;

I understand the rt2870 is in the 2.6.31 kernel already;

so I sense that is the way to go;

if one installs ndiswrapper, I understand you then need to remove or blacklist it, if you use the rt2870;

see if any of the post above helps you; it is current on this forum;

it would be wonderful if everything in linux just happened; sometimes things require a little help; and you learn about your system, and may well then be able to help others

---

### Post by echorequest on 2010-01-25
ok thanks for the reply.  what a dolt I am. Its one or the other, not both. I will read through that link you posted.

---

### Post by tomcogc on 2011-01-12
> **echorequest said:**
> Hello,Iam trying to get my Zonet ZEW2500P usb going. I installed the windows .inf file off the CD.some output:da@da-ASUS:~$ lsusbBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 007 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel MouseBus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubda@da-ASUS:~$ ndiswrapper -lWARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.rt2870 : driver installeddevice (148F:3070) present (alternate driver: rt2800usb)da@da-ASUS:~$ iwconfiglo no wireless extensions.eth0 no wireless extensions.da@da-ASUS:~$ lsmodModule Size Used byndiswrapper 185692 0 binfmt_misc 8356 1 ppdev 6688 0 snd_hda_codec_atihdmi 3356 1 snd_hda_codec_realtek 203328 1 snd_bt87x 12708 1 snd_hda_intel 26984 2 snd_hda_codec 75708 3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hd a_intelsnd_hwdep 7200 1 snd_hda_codecsnd_pcm_oss 37920 0 snd_mixer_oss 16028 1 snd_pcm_osssnd_pcm 75520 4 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_osstda18271 35556 1 lgdt3305 12256 1 snd_seq_dummy 2656 0 tuner_simple 14832 1 tuner_types 14396 1 tuner_simplesnd_seq_oss 28576 0 snd_seq_midi 6432 0 snd_rawmidi 22208 1 snd_seq_midisnd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midisnd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_eventsnd_timer 22276 2 snd_pcm,snd_seqsnd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seqasus_atk0110 8252 0 lp 8964 0 parport 35340 2 ppdev,lptuner 21540 1 tvaudio 25884 0 tda7432 5016 0 msp3400 28204 0 bttv 119412 0 ir_common 48512 1 bttvi2c_algo_bit 5760 1 bttviptable_filter 3100 0 ip_tables 11692 1 iptable_filterx_tables 16544 1 ip_tablescx23885 100444 0 cx2341x 13440 1 cx23885videobuf_dma_sg 12608 2 bttv,cx23885v4l2_common 17500 7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,cx2341xvideodev 36736 7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,v4l2_co mmonv4l1_compat 14496 1 videodevvideobuf_dvb 7040 1 cx23885dvb_core 87364 3 lgdt3305,cx23885,videobuf_dvbvideobuf_core 17952 4 bttv,cx23885,videobuf_dma_sg,videobuf_dvbbtcx_risc 4772 2 bttv,cx23885tveeprom 11872 2 bttv,cx23885snd 59204 19 snd_hda_codec_realtek,snd_bt87x,snd_hda_intel,snd_ hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_ pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_ seq_[[COLOR=#000000]device[/COLOR]](http://www.****************.com/mpeg4-video-format/convert-mxf-video-to-mpeg4-format.html)fglrx 1989980 34 soundcore 7264 1 sndsnd_page_alloc 9252 3 snd_bt87x,snd_hda_intel,snd_pcmfloppy 54980 0 usbhid 38304 0 atl1e 31888 0 intel_agp 27748 0 agpgart 35020 2 fglrx,intel_agpda@da-ASUS:~$ lsmodModule Size Used byndiswrapper 185692 0 binfmt_misc 8356 1 ppdev 6688 0 snd_hda_codec_atihdmi 3356 1 snd_hda_codec_realtek 203328 1 snd_bt87x 12708 1 snd_hda_intel 26984 2 snd_hda_codec 75708 3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hd a_intelsnd_hwdep 7200 1 snd_hda_codecsnd_pcm_oss 37920 0 snd_mixer_oss 16028 1 snd_pcm_osssnd_pcm 75520 4 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_osstda18271 35556 1 lgdt3305 12256 1 snd_seq_dummy 2656 0 tuner_simple 14832 1 tuner_types 14396 1 tuner_simplesnd_seq_oss 28576 0 snd_seq_midi 6432 0 snd_rawmidi 22208 1 snd_seq_midisnd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midisnd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_eventsnd_timer 22276 2 snd_pcm,snd_seqsnd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seqasus_atk0110 8252 0 lp 8964 0 parport 35340 2 ppdev,lptuner 21540 1 tvaudio 25884 0 tda7432 5016 0 msp3400 28204 0 bttv 119412 0 ir_common 48512 1 bttvi2c_algo_bit 5760 1 bttviptable_filter 3100 0 ip_tables 11692 1 iptable_filterx_tables 16544 1 ip_tablescx23885 100444 0 cx2341x 13440 1 cx23885videobuf_dma_sg 12608 2 bttv,cx23885v4l2_common 17500 7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,cx2341xvideodev 36736 7 tuner,tvaudio,tda7432,msp3400,bttv,cx23885,v4l2_co mmonv4l1_compat 14496 1 videodevvideobuf_dvb 7040 1 cx23885dvb_core 87364 3 lgdt3305,cx23885,videobuf_dvbvideobuf_core 17952 4 bttv,cx23885,videobuf_dma_sg,videobuf_dvbbtcx_risc 4772 2 bttv,cx23885tveeprom 11872 2 bttv,cx23885snd 59204 19 snd_hda_codec_realtek,snd_bt87x,snd_hda_intel,snd_ hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_ pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_ seq_devicefglrx 1989980 34 soundcore 7264 1 sndsnd_page_alloc 9252 3 snd_bt87x,snd_hda_intel,snd_pcmfloppy 54980 0 usbhid 38304 0 atl1e 31888 0 intel_agp 27748 0 agpgart 35020 2 fglrx,intel_agpda@da-ASUS:~$ When i use the wireless network drivers gui (ndisgtk)it shows the rt2870 driver and that the hardware is present.clicking on the configure network button i get a message: "could not find a network configuration tool"Any suggestions to try would be appreciated.It's comprehensive, Thanks for your sharing! It's helpful to me.

---

