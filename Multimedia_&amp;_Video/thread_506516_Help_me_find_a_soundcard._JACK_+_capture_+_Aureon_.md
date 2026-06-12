---
title: "Help me find a soundcard. JACK + capture + Aureon 7.1 PCI = no love... I think"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by mrowth on 2007-07-21
I was happy to have JACK running in Realtime with the low latency kernel, ALSA, and my on-board VIA 8237 sound"card", but the sound itself still wasn't too great (some distortions and crackling at high volumes). 

So I picked up an affordable-by-me card that was listed as supported by the ALSA Soundcard Matrix - the Terratec Aureon 7.1 PCI.

I haven't seen a new soundcard in years and am a little confused. Very, actually. [SIZE="1"]The mixer seems to be missing a number of sliders: the only Output channels in Kmix are Master, Phone and PC Speaker.(For my on-board sound they're: Master, Master Mono, PCM, Surround, Center, LFE, IEC958 Playback AC97-SPSA, PC SPeaker, VIA DXS, VIA DXS, VIA DXS, VIA DXS). No PCM/Wave? Input doesn't even have a Capture slider, is that the way it's supposed to be? There're a number of sliderless "mere" switches though so perhaps you're not expected to adjust anything here?
[/SIZE]
[COLOR="DarkOrchid"]**More importantly, JACK won't work**[/COLOR]

Starting JACK: 
[B]
the capture device "hw:0,0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa[/B]

But there is no application using it. I can start JACK playback-only or capture-only, but what's the point?

**[COLOR="DarkOrchid"]Some command outputs that I could think of[/COLOR]**

```
[B][U]
cat /proc/asound/cards[/U][/B]

 0 [CMI8738MC8     ]: CMI8738-MC8 - C-Media PCI CMI8738-MC8
                      C-Media PCI CMI8738-MC8 (model 68) at 0xb400, irq 22
 1 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0x1000, irq 21
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x300, irq 10
 3 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xdff00000, irq 19

**[B]_arecord -l_**[/B]

**** List of CAPTURE Hardware Devices ****
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Bt878 [Brooktree Bt878], device 0: Bt87x Digital [Bt87x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Bt878 [Brooktree Bt878], device 1: Bt87x Analog [Bt87x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  
**_aplay -l_**

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1

**_lshw -class sound_**

  *-multimedia:0          
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: d
       bus info: pci@00:0d.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=C-Media PCI latency=64 maxlatency=24 mingnt=2
       resources: ioport:b400-b4ff irq:22
  *-multimedia:1
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: e
       bus info: pci@00:0e.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=bttv latency=64 maxlatency=40 mingnt=16
       resources: iomemory:dfe00000-dfe00fff irq:19
  *-multimedia:2
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: e.1
       bus info: pci@00:0e.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Bt87x latency=64 maxlatency=255 mingnt=4
       resources: iomemory:dff00000-dff00fff irq:19
  *-multimedia:3
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=VIA 82xx Audio latency=0
       resources: ioport:1000-10ff irq:21


```

So I don't know... should I return the card to the store and buy another one that presumably won't work either... is there something I can do to make this work?

---

### Post by fredj on 2007-07-21
Open the Alsa mixer by double clicking on the speaker icon in the system tray. Go to the File->Change Device
menu and make sure that your soundcard with Alsa is selected as the default device.
Go to the Edit->Preferences menu and add all the necessary volume/switch controls for playback and record.

---

### Post by mrowth on 2007-07-22
> **fredj said:**
> Open the Alsa mixer by double clicking on the speaker icon in the system tray. Go to the File->Change Device
menu and make sure that your soundcard with Alsa is selected as the default device.
Go to the Edit->Preferences menu and add all the necessary volume/switch controls for playback and record.

Thanks, but that's not the problem. Everything's using the same (and correct) card.

There're no additional volume controls left to turn on, either; even if there were, I don't think those would interfere with JACK running in duplex mode. It's either playback-only or capture-only, which is useless to me.

(I've turned everything on in this screenshot, but it doesn't matter. I can turn it all off, same result)

---

### Post by mrowth on 2007-07-22
And here're my qjackctl setup (attachment) and its output of doom

mrowth@earthworm:~$ jackd -R -p128 -dalsa -r48000 -p128 -n2 -D -Chw:0,0 -Phw:0,1 -S
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,1|hw:0,0|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
[B]the capture device "hw:0,0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
Segmentation fault (core dumped) 
[/B]

Here's me starting it with the on-board sound:

mrowth@earthworm:~$ jackd -R -p128 -dalsa -r48000 -p128 -n2 -D -Chw:1,0 -Phw:1,1 -S
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1,1|hw:1,0|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:1
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

---

### Post by kvonb on 2007-07-22
You might want to disable your onboard sound card from your computer's BIOS, it will only confuse things otherwise.

This is a really great thread for sound issues:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

You might find a solution there :)

---

### Post by mrowth on 2007-07-22
> **kvonb said:**
> You might want to disable your onboard sound card from your computer's BIOS, it will only confuse things otherwise.
I've disabled it, actually. It still shows up (it's actually useful in that an available working soundcard lets me double-check if things are working "in principle")
> This is a really great thread for sound issues:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

You might find a solution there :)
I've got that one bookmarked ;) but it seems more concerned with getting sound to play at all, enabling mixer controls, or stopping multiple cards from "switching around" etc...then again, it's over 60 pages...

---

### Post by fredj on 2007-07-22
This is a very strange problem because the sound card you have is very well supported in Alsa and is
also very common so that fact that it won't work as a duplex card would by now have been well reported.
Am I right in thinking that you also have a video capture card installed? If so perhaps you could temporarily
remove it and see if you can get your sound card working.

---

### Post by mrowth on 2007-08-04
Thanks for your reply. Yes, I have a Hauppauge WinTV card for the VCR. Removing it didn't make a difference either.

Sound in Linux sure ain't easy... for now, the onboard soundchip will have to do. I just took the card back to the story for a refund.

Thanks to everyone who tried to help!

---

