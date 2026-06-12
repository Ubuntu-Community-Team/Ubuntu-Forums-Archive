---
title: "[SOLVED] No sound after upgrade to Gutsy"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Kylotan on 2008-08-27
Hello all,

I recently upgraded my Kubuntu from 7.04 to 7.10, which was a rather troublesome process. After the initial update from the GUI kept crashing, I managed to complete the update from the command line, and then had to change the video driver after the reboot as my old Nvidia ones wouldn't work. My next problem is that now my sound doesn't work - I hear no output whatsoever, from either the onboard sound card or my add-on sound card (though only the latter matters, really). I vaguely remember having to do something with modules to get it to work in the first place, but I have no idea what.

Since I don't know what is relevant, I'll dump some command output here and will happily provide other outputs if requested.


> uname --all
Linux rapture 2.6.22-15-generic #1 SMP Fri Jul 11 19:25:33 UTC 2008 i686 GNU/Linux

> cat /proc/asound/cards
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbffc000 irq 26
 1 [default        ]: USB-Audio - Samson C01U
                      Samson Technologies       Samson C01U               at usb-0000:00:10.0-2, full
 2 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xec00, irq 27

> lspci
[...loads of probably irrelevant stuff omitted...]
07:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
08:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> aplay -vv /media/sdb1/music/test.wav
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such file or directory

>  lsmod | grep snd
snd_ice1712            65140  1
snd_ice17xx_ak4xxx      5120  1 snd_ice1712
snd_ak4xxx_adda         8832  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9984  1 snd_ice1712
snd_ac97_codec        100644  1 snd_ice1712
ac97_bus                3200  1 snd_ac97_codec
snd_i2c                 6656  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9600  1 snd_ice1712
snd_usb_audio          81024  1
snd_usb_lib            17920  1 snd_usb_audio
snd_hwdep              10244  1 snd_usb_audio
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_hda_intel         263840  1
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25728  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_pcm                80388  5 snd_ice1712,snd_ac97_codec,snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_timer              24324  2 snd_seq,snd_pcm
snd                    54660  23 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_usb_audio,snd_hwdep,snd_seq_oss,snd_hda_intel,snd_seq,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
usbcore               138632  7 snd_usb_audio,snd_usb_lib,usbhid,xpad,ehci_hcd,uhci_hcd


Hopefully some of that is relevant!

---

### Post by arch0njw on 2008-08-27
I have followed the steps at these threads and gotten sound back:

[http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/)
[http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html](http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html)

For some reason almost every time I upgrade, I lose sound.

---

### Post by Kylotan on 2008-08-27
Hey arch0njw, the suggestion in the first link to use asoundconf set-default-card with the card you want did the trick! I had speakers plugged into both my sound cards before, so I can only assume it was trying to use an input device like my USB microphone as an output: rather unfortunate!

Thanks for your help.

---

### Post by arch0njw on 2008-08-28
Excellent!  Please mark the thread as solved.  Glad to "hear" you have sound back.  :)

---

