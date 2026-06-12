---
title: "[SOLVED] Problem connecting USB Audio Device with Jack"
date: 2008-08-18
forum: Multimedia Software
---

### Post by BlackCat13 on 2008-08-18
Problem: Cannot see my USB audio connection in Jack or Ardour to patch it.

History: I have a home studio that I use for recording my partner and I (simple vocals and guitar with Bass and Drum overlays) and then creating demo audio CD's for distribution. I have been using Windoze for this with Cubase, Ableton and various others. I use a xenyx2442 to mix down currently (yes it's crap but my Mackie 1604 (USA made) got stolen - long story - and it is all I can afford atm) and feed it into my laptop through a Yamaha GO46 (firewire interface). I run a dual boot with Vista (groan). I now do everything on Hardy EXCEPT recording and I would love to be able to get this final hurdle handled (so I can run madly down the street screaming "I'm Free, I'm Free"). I have Jack running and configured for my onboard Intel card using RT Kernel, I can rock away happily on Hydrogen and record the result nicely in Ardour, I just can't get any vocals or guitar :( recorded. I am NOT trying to get the GO46 happening at this stage (although if someone could assist with this it would be fantastic) I am resigned to using it as a paperweight. I however thought I would try my never before used U-Control UCA200 usb connector that came with the mixer. I have seen a few posts around mentioning this device but they all say that it plugged and played (mine just plugged >.<) I know that the audio device is recognised in the system as it is listed when I aplay -l. It also shows up in Jack Control Setup as an option on Interface/Input Device and Output Device but if I choose it then the Jack Server goes xRun crazy again. I think I am close to getting it working but I don't know enough about how Linux works with sound and I don't really know what I am doing in Jack Control Setup (Is there a comprehensive writeup or manual anywhere for this!)

I have attached a screenshot of my Jack Setup showing the InterFace control options and my general settings. 

Other: Here is the readout from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Note: Is it weird that card 1 is listed as default? Just a question...

I am not sure what other information might be required (and this already rivals TWoT in length so I will post and hope that someone can assist me in my quest to remove the Windoze virus that I have had for years...)

(P.S. I am not really a Windoze hater... it has served me well over the years. But I have been trying to shift to Linux (unsuccessfully) since 1998 and I am happy to say that using Hardy I now am finished with the other OS for good except for this. I am sarcastic btw but you probably figured that :) thanks.)

---

### Post by BlackCat13 on 2008-08-19
OK so an update... after taking a break and clearing the head I played around with the Jack settings just a little and voila I have audio in in Ardour... now I just need to learn how the program thinks... so I am calling this solved

---

