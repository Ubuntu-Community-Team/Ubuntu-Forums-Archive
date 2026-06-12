---
title: "sound not working since dist-upgrade to dapper"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by taniwhaiti on 2006-06-09
i dist-upgraded from breezy to dapper, i386

now sound systems sez it's working but there's no sound 

i'm unsure what to do next...

i've got 2 sound cards. An onboard one that's teh suck.. and a nice PCI once.
below it looks like it only found one of them (and my usb camera)
> 
$ cat /proc/asound/cards
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xdc00, irq 177
1 [Camera         ]: USB-Audio - USB Camera
                     OmniVision Technologies, Inc. USB Camera at usb-0000:00:07.2-1.1, full speed



playing a file in amarok, there's no errors - it appears to be playing but there's no sound coming out of either sound card.

i've checked my speakers work (with my ipod) - they work.
i've looked and volume is not muted in kmix.

> 
$ sudo adduser shiny audio
The user `shiny' is already a member of `audio'.


> 
$ lsmod | grep snd
snd_usb_audio          78912  0
snd_usb_lib            16640  1 snd_usb_audio
snd_cmipci             34336  5
gameport               15496  1 snd_cmipci
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  5 snd_usb_audio,snd_cmipci,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cmipci
snd_timer              25220  4 snd_pcm,snd_opl3_lib
snd_hwdep               9376  2 snd_usb_audio,snd_opl3_lib
snd_mpu401_uart         7808  1 snd_cmipci
snd_rawmidi            25504  2 snd_usb_lib,snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd                    55268  17 snd_usb_audio,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3
_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
usbcore               129668  7 snd_usb_audio,snd_usb_lib,ov511,usb_storage,usbhid,uhci_hcd


---

