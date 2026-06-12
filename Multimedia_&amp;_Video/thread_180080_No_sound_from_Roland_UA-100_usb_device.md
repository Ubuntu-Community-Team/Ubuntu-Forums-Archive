---
title: "No sound from Roland UA-100 usb device"
date: 2006-05-21
forum: Multimedia &amp; Video
---

### Post by smetoyer on 2006-05-21
I'm having some difficulty get ALSA sound to work with a Roland UA-100... Bear with me I'm a bit of a newb.  The driver appears to load ok, however aplay will hang when trying to play any wave files (doesn't play any sound, has to be forcibly ended).  Attempting to test in the Multimedia Systems Selector results in the 'Failed to construct test pipeline for Alsa' message.

Here's the results of aplay -l:

```
card 0: UA100 [UA-100], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

and the results of lsmod | grep snd:

```
        snd_usb_audio       68160  3
snd_pcm_oss         46368  0
snd_mixer_oss        16128  2 snd_pcm_oss
snd_pcm               78344  3 snd_usb_audio,snd_pcm_oss
snd_page_alloc       10120  1 snd_pcm
snd_usb_lib            13824  1 snd_usb_audio
snd_hwdep             8608  1 snd_usb_audio
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  13 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd
usbcore               104316  5 snd_usb_audio,snd_usb_lib,ndiswrapper,uhci_hcd

```
and a cat /proc/asound/cards:

```
0 [UA100          ]: USB-Audio - UA-100
                     Roland UA-100 at usb-0000:00:1f.4-2.2, full speed
```

TIA for any help getting this thing working!

---

