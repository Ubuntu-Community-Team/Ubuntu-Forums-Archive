---
title: "Surround sound - grr..."
date: 2006-04-04
forum: Multimedia &amp; Video
---

### Post by Sonique on 2006-04-04
I am having difficulty in getting surround sound to work, and it is really annoying that I might go back to windows again just to have it. I can get the front left and front right and the woofer to work, but the center and back right and left are silent. I have "Logitech® X-530" speaker system as shown in this picture: [here]("http://www.logitech.com/lang/images/0/4219.jpg"). 
I tried this thread: [here]("http://www.ubuntuforums.org/showthread.php?t=44753&highlight=surround+sound") but i couldnt get it to work, all i got out of it was that when i go to applications>sound&video>volume control, i have two devices in "file>change device" (ALSA and OSS). I turned every control up and nothing changes.

Here are some things that might be useful:
```
$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

```
$ lsmod | grep snd
snd_intel8x0           30144  5
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

```

Any other information that you might need to solve this, please ask me. I really want to get my system up. (I am using Ubuntu Breezy atm)

---

### Post by DutchR_PW on 2006-04-04
Have you tried the "Mirror Front" switch (I don't know what it is called exactly) in the mixer?

---

### Post by Sonique on 2006-04-04
Hmm.. can see a switch like that. In the switches tab, i have the following:

Master
Mic Boost
IEC958 Capture Monitor
IEC958 Capture Valid
External Amplifier

Cheers for your help so far

---

### Post by DutchR_PW on 2006-04-04
The Gnome mixer hides a lot of switches by default, there is an option somewhere in the menu bar of the mixer which lets you choose what to show.

You can also try alsamixer (run it from a terminal) which doesn't hide anything.

---

### Post by Sonique on 2006-04-09
This is really strange, i did "alsamixer" in the terminal and i adjusted all of the everything and none of them make a difference to the volume apart for one thing: PCM if you mute it then the sound goes off, but if you adjust the volume nothing happens. I remember in windows, I had to get a driver to get it to work.

I don't understand any of this :-?

---

