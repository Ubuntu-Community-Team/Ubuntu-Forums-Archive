---
title: "Activate HDMI Bitstream Audio (audio passthrough) to reciever"
date: 2015-05-13
forum: Multimedia Software
---

### Post by luke45 on 2015-05-13
Hello, 

has anyone successfully sent bitstream HD audio from a linux system via HDMI to an A/V receiver? 

My set up is as follows:

CPU: Intel Pentium G3240
MOBO: Asus B85-M G
Receiver: Onkyo HT-R693
OS: Currently have elementary os freya installed as I couldn't figure out bitstreaming in Ubuntu 14.04 (Then I realised elementary os is basically a redesigned ubuntu).

The only options for audio output seem to be 'built in audio'. I tried through VLC and Kodi but no luck. 

Any help would be much appreciated as I am an Ubuntunoob and i have only just got my reciever and computer and I just want to listent to TRUE HD LOSSLESS audio.

thanks in advance!

---

### Post by blm-ubunet on 2015-05-14
Plenty have but maybe not with your h/w (intel cpu/gpu).

Install & run "pavucontrol" to find what audio options you have & configure them.
It is possible pulseaudio can't support True HD bitstream yet.

Kodi/mythtv/vlc are capable of using the alsa audio devices directly.

Try launching kodi with
```
AE_SINK=ALSA kodi
```

You may need to consider the "hardware enablement stack" to get this working on recent intel cpu/gpus.
Need read the fine print about subsequent upgrade paths if you do.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by luke45 on 2015-05-15
Thanks you got me onto the right track. In the end I reinstalled Ubuntu and properly configured pulseaudio for bitstreaming. You are right though, pulseaudio cannot bitstream DTS HDMA or Dolby TrueHD so thanks for the work around, Ill use alsa for those titles. I read somewhere that opening KODI the way you suggested can have negative effects, so far no problems here. Thanks again!

---

### Post by blm-ubunet on 2015-05-15
Great..
Not sure why it has taken pulseaudio so long to support bitstreamed/pass-thru' audio formats.
Support for AC3/DTS was years after alsa support.
Probably just lack of hardware/time/finance.

But on a positive note, pulseaudio has never caused me problems with using alsa directly.
MythTV (& likely Kodi) can disable pulseaudio server.

---

