---
title: "a little help with Xawtv configuration?"
date: 2008-10-09
forum: Multimedia Software
---

### Post by cake_or_death on 2008-10-09
Xawtv is the only program that will recognize the integrated webcam on my vaio-cr.  I can see myself, and snap photos, but haven't been successful in recording any video so far.  I don't know how to go about creating a configuration file for the program, and I'm guessing that may be what's causing the problem.  Anybody have some pointers for configuring Xawtv?

---

### Post by cake_or_death on 2008-10-16
anybody?

---

### Post by joshua1091 on 2009-02-01
hi i installed xaw tv in my pc...
video is working fine
audio from tv tuner card is fine(but low in volume) when i hear with headphone joined to the card

**but now i have connected the audio out of the tv tuner to line in of audio card**

**OS-ubuntu 8.04 hardy heron**

in sound preferences i have set **"OSS open sound system"** for all options

for default mixer tracks i set **"sigmatel stac9221 A1 (OSS mixer)"**

when i run xaw tv and _click "test" button_ next to "sound capture" in "sound preferences" _i could hear the audio_ from my ps2 in the speakers connected to my pc

in xawtv,

video source=composite2 //my ps2 video input

i think i have to fill in the mixer = <value> in  /etc/x11/xawtvrc,but i dont know what value to fill

here is the description of my tuner card:

product: SAA7130 Video Broadcast Decoder
vendor: Philips Semiconductors
physical id: 1
bus info: pci@0000:05:01.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15 module=saa7134

here is the list of sound cards: got using "cat /proc/asound/cards"

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x72100000 irq 22
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7130[0] at 0x72001000 irq 22

here is the list of modules: got using  "cat /proc/asound/modules"

 0 snd_hda_intel
 1 saa7134_alsa

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


please help me solve the problem,tell me what will be the value opposite to mixer field

---

