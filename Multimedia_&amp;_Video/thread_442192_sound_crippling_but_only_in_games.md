---
title: "sound crippling but only in games"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by tommi on 2007-05-13
Hello,

i have a problem with sound in games. i have an dell xps m1210 with ich7.

```

thomas@thomas-laptop:~$ lsmod | grep snd
snd_rtctimer            4384  0
snd_hda_intel          21912  1
snd_hda_codec         205440  1 snd_hda_intel
snd_seq_dummy           4740  0
snd_usb_audio          79744  1
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_oss            32896  0
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_usb_lib            17280  1 snd_usb_audio
snd_rawmidi            25472  2 snd_seq_midi,snd_usb_lib
snd_hwdep               9988  1 snd_usb_audio
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
usbcore               134280  9 xpad,snd_usb_audio,uvcvideo,usbhid,hci_usb,snd_usb_lib,ehci_hcd,uhci_hcd

```

i hear problems in Secret Maryo Chronicles 2D platform game, in zsnes, in super mario tux. i think all games use SDL .. is there a way to test the soundoutput of sdl or to configure SDL ?

or is the error not in sdl ? Amarok works, aplay works, kaffeine works (audio / video all works) but not games .. hwo i can test ?

have windows installed to play zsnes with sound, thats not good :) sry for bad english

---

### Post by gborzi on 2007-05-13
I had a similar problem with a game that uses the openal sound library. I don't know if the games you listed use this library, anyway the fix in this case is to create a file in your home directory named .openalrc > gedit ~/.openalrc with the following content > (define devices '(esd alsa arts native))
Hope this helps.

---

