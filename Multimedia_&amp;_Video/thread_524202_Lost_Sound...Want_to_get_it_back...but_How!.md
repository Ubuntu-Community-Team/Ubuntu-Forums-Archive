---
title: "Lost Sound...Want to get it back...but How?!?"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by JockVSJock on 2007-08-12
Installed Ubuntu 7.04 on my Averatec laptop. 

I want to record my synth via midi interface to the laptop...The sound used to work, but now it doesn't.  Well, when I test the sound, I can barely hear it.  Here is my setup: 

```

root@probot:~# alsamixer -V
alsamixer: option requires an argument -- V
AlsaMixer v1.0.13


root@probot:~# alsactl -V
alsactl version 1.0.13


root@probot:~# lsmod | grep snd
snd_rtctimer            4384  0 
snd_via82xx            29208  5 
gameport               16520  1 snd_via82xx
snd_mpu401_uart         9472  1 snd_via82xx
snd_usb_audio          79744  2 
snd_usb_lib            17280  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_hwdep               9988  1 snd_usb_audio
snd_seq_midi            9600  3 
snd_rawmidi            25472  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_via82xx_modem      16008  0 
snd_ac97_codec         98464  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  7 snd_via82xx,snd_usb_audio,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq                52592  15 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  24 snd_via82xx,snd_mpu401_uart,snd_usb_audio,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore               8672  1 snd
usbcore               134280  5 snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd


```

I saw this thread, 

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

But haven't gone thru it yet to troubleshoot.  Can anyone make any suggestions? 

thanks

---

