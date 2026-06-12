---
title: "Cant get my Terratec USB MKII soundcard to work!"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by hobs0n on 2007-06-27
I havent gotten my Terratec USB MKII soundcard to work. I have it connected by the Optical Out to the Optical In on my stereo and I tried the headphone output and no sound in either of them. I asked a person called george_apan about it since he have the same soundcard but he didnt know what to do. He told me to run "lsmod | grep snd_usb_audio" to get some info and I did and this is what it said:

[I]snd_usb_audio 94336 0
snd_pcm 92808 2 snd_usb_audio, snd_pcm_oss
snd_usb_lib 19584 1 snd_usb_audio
snd_hwdep 12168 1 snd_usb_audio
snd 68904 10 snd_usb_audio, snd_pcm_oss, snd_mixer_oss, snd_pcm, snd_hwdep, snd_seq_oss, snd_rawmidi, snd_seq, snd_timer, snd_seq_device

usbcore 154416 7 snd_usb_audio, snd_usb_lib, xpad, usbhid, ehci_hcd, ohci_hcd[/I]

Anyone know whats wrong?

---

### Post by hobs0n on 2007-06-28
anyone?

---

