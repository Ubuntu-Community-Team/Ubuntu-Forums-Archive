---
title: "VERY odd sound problem on inspiron 9100"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by coleman on 2007-10-04
The speakers on my Inspiron 9100 will not play any sound, but my headphones work perfectly.  I have tried playing around in alsamixer but nothing seems to work.  I think the problems started when I was playing around with Ardour and Jack as I am into mixing and editing audio.  Here is all my standard info.


:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with STAC9750,51 at 0xf8fff800, irq 17

~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with STAC9750,51 at 0xf8fff800, irq 17
 1 [MI4            ]: USB-Audio - MI4
                      Steinberg MI4 at usb-0000:00:1d.3-1, full speed

~$ lsmod|grep snd
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_intel8x0           34332  0 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_pcm                79876  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
usbcore               134280  8 snd_usb_audio,snd_usb_lib,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd

---

### Post by Steggie on 2007-10-24
Hi thought you might like to compare mine. I also use an Inspiron 9100  with no sound trouble.

$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with STAC9750,51 at irq 17

$ lsmod|grep snd
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


I notice yours is using a usb soundcard could there be a conflict?

---

