---
title: "Lubuntu 14.04 USB sound crackly (ALSA issue)"
date: 2014-04-24
forum: Multimedia Software
---

### Post by garethfoxwilliams on 2014-04-24
I have put Lubuntu 14.04 on several machines:

On a Fujitsu Lifebook, the audio is fine, both on the internal and USB (Edirol UA-1X) sound cards:
```
 -LIFEBOOK-T4210:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0640000 irq 45
 1 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1d.0-1, full speed

```

On a Dell Mini 1210, the USB audio has been crackly, with digital artifacts / buffering splats.

```
Inspiron-1210:~$  cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xd83a0000 irq 22
 1 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:1d.1-2, full speed
 
```

For once, I know the problem isn't Pulseaudio.

On the Mini 1210, I can install Jack and, with a framerate of 1024, Period/Buffer 3, giving a latency 69.7 msec, I can minimize the artifacts with few(ish) XRUNs, but this is still not great, and not up to pro standard.

I am using Audacious as the media player, and 320kbps/44.1kHz mp3 files.

Has anyone got any suggestions as to some more parameters to tweak, or suggestions as to why the 1210 isn't coping?

---

### Post by garethfoxwilliams on 2014-04-26
Further investigations:

With Jack settings of f/r = 4096, Periods/Buffer = 2,  sample rate = 48000 ( Edirol's highest) I still get an audible XRUN every couple of minutes, in addition to occasional crackling that sounds like a vinyl disk. 

With Jack settings of f/r = 4096, Periods/Buffer = 2,  sample rate = 96000, I get clean sound on the internal audio via headphones, but still an XRUN every minute and a half, or so. 

I have tried the buffer in Audacious at the defaut 100ms and the next setting up, 1000ms, but I'm not sure how that setting interacts with the buffer in Jack.

Am I wrong to expect better performance out of a netbook ???

- the spec of which is:

CPU Intel ® Atom 1.6GHz
Chipset Intel LPIA Poulsbo US15W
1GB 533 MHz DDR2 RAM

---

### Post by garethfoxwilliams on 2014-04-27
I have found solutions to both of my issues!

**Firstly, the XRUN issue, **which affected both internal and external sound cards, was fixed with the help of this thread: 

[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

 ...and adding the line ```
options snd-hda-intel position_fix=1
```

to the bottom of /etc/modprobe.d/alsa-base.conf 

 ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

**Secondly, the crackling similar to the clicks and pops of an old vinyl record which were on the USB sound card, but not the internal sound device.**

 I eventually discounted a sample rate issue and narrowed it down to a power-saving device issue....

 When the USB dongle was handling the audio, the CPU experienced less load than with the internal sound device and was therefore switching in and out of power save mode, causing clicks on the audio.

This page set me onto the right trail: 

[http://askubuntu.com/questions/175602/periodic-clicking-sound-from-pc-speaker/195800#195800](http://askubuntu.com/questions/175602/periodic-clicking-sound-from-pc-speaker/195800#195800)

 I confirmed this by opening Firefox and downloading a large file which gave the CPU some work to do and stopped the power switching, cleaning up the audio. I and others had also noticed a similar thing whereby the audio became clean when Pulse Audio Volume Control was open, but became crackly when it closed. 

I disabled this power saving feature, called **Intel (R) SpeedStep (TM) Technology  **feature in the BIOS/setup ( see picture ) and the audio is now clean.

[ATTACH=CONFIG]252575[/ATTACH]

---

