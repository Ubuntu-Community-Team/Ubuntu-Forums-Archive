---
title: "Soundblaster SB0490 USB problems"
date: 2010-06-24
forum: Multimedia Software
---

### Post by Graemej on 2010-06-24
I have a Creative SoundBlaster live SB0490 USB sound card. Alsamixer only shows a mic channel for this card although it has a line in. Is this because it is not supported or how it is meant to be? I have problems with no audio out on a program which directly accesses the card as hw:1 although it is actually using it and wonder if this is all related. Strangely I can play sound through the card using rythmbox.

To aid anyone who may be able to help here is all the audio details I can figure out.

Thanks in anticipation, Graeme

```
uname -a
Linux gvj-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
gvj@gvj-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gvj@gvj-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
gvj@gvj-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa
gvj@gvj-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
gvj@gvj-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 29
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:1d.1-1, full speed
gvj@gvj-laptop:~$ 

```

---

### Post by Graemej on 2010-06-25
Don't seem to be having much luck. Maybe someone can tell me if this is all I should see on this card with alsamixer. With a line in and a mic I would have expected to see them on the mixer and also a master on play.

Screenshot below   ...   Thanks Graeme

---

### Post by lidex on 2010-06-25
You should have a look here:
[http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio")

---

### Post by Graemej on 2010-06-25
Hi Lidex,

Thanks for reply. I am working through Takashi Iwai's article and have run up against some further questions.

I have installed alsa previously using the script in your signature so I assume I don't need to go through the alsa install in the first part of the article. Right or wrong?

There is no modules.conf or conf.modules in my /etc but there is a modules file. Is this the new format for modules.conf or am I missing it?

When doing the modprobes I get warning messages as shown below. Are these safe to ignore?

Are the messages associated with no modules.conf?

```

gvj@gvj-laptop:~$ modprobe snd-usb-audio
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
gvj@gvj-laptop:~$ modprobe snd-pcm-oss
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
gvj@gvj-laptop:~$ modprobe snd-mixer-oss
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
gvj@gvj-laptop:~$ modprobe snd-seq-oss
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
gvj@gvj-laptop:~$

```

I have not proceeded beyond here as I don't want to bork my sound system yet again although I have now lost my fear of putting it back together.

Thanks, Graeme

---

### Post by lidex on 2010-06-25
Should be safe to ignore. He makes some note of the fact that different distros have moved some things around, so files may appear in different locations.

---

