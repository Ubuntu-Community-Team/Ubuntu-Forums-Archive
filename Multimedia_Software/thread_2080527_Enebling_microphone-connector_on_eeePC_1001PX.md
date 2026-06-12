---
title: "Enebling microphone-connector on eeePC 1001PX"
date: 2012-11-04
forum: Multimedia Software
---

### Post by resruta on 2012-11-04
Hi there,

this is my first post in this forum and I directly have a question concerning the audio-settings on my Asus eeePC 1001PX, which has a combined headphones out/mic in connector.
What I'm trying to do is using the connector for some quick recordings out of a small mixing desk (I'm absolutely aware of the fact that I cannot expect high quality recordings  with that A/D-converter, we only need these recordings in a band for self evaluation).

I now have the problem that I do not know how to access this dual connector as a capture device?

Here's some more background:
I spoke with the Asus support, they said that its some kind of "ether/or" connector, so it's not the case that I just have to use a 4-pole jack. 
They also said that the driver should somehow recognize whether the connector has to be addressed as a line in or line out. Unfortunately they do not support Linux systems.

I'm using Lubuntu 12.04 32bit with the universe *lowlatency*-Kernel, using *jack* for some audio applications, apart from that ALSA. Pulseaudio is not installed, nor is esd or arts.
I tried playing with the settings in *alsamixer, *I tried the different capture-devices in *qjackctl *but every listed device only contains the signal out of the integrated microphones.
I've tried both modes *laptop-amic* and *laptop-dmic* mentioned in **/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt **without success.

Here is some more information about the system:
```
$ **cat /proc/asound/cards**

0 [Intel          ]: HDA-Intel - HDA Intel
                       HDA Intel at 0xf7cf8000 irq 45
``````
**$ head -n 1 /proc/asound/card0/codec* **

Codec: Realtek ALC269
``````
**$ lspci -nnk | grep -iA2 audio**

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8442]
    Kernel driver in use: snd_hda_intel
``````
**$ lsmod | grep "snd"c* **

snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```And the AlsaInfo: [http://www.alsa-project.org/db/?f=a522a3aa1d02fc7aa2ee666893a5baea0b467b63](http://www.alsa-project.org/db/?f=a522a3aa1d02fc7aa2ee666893a5baea0b467b63)[URL="http://www.alsa-project.org/db/?f=7489c290100240847934391fc7f6e6c174d5221a"]
[/URL]
I'm sorry for my bad English, I'm from Germany :)

Thanks a lot for your help in advance,
Joe

---

### Post by Yellow Pasque on 2012-11-04
It sounds like this may help: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by resruta on 2012-11-04
Thank you so much for that hint.
This tool is awsome and instantly solved my problem.

Thank you !

---

### Post by Yellow Pasque on 2012-11-04
You're welcome. Enjoy!

---

