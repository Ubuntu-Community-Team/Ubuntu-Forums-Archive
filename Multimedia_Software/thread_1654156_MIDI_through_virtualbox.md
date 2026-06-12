---
title: "MIDI through virtualbox"
date: 2010-12-27
forum: Multimedia Software
---

### Post by EverythingIsNothing on 2010-12-27
I have a Tascam US-144mkii controller.
I'd like to get MIDI through it but this seems impossible natively so is there any way I can virtualbox install a stripped Windows XP and somehow forward the MIDI from virtualbox to my linux host?

Thanks in advance

---

### Post by cchhrriiss121212 on 2010-12-28
That would be a very inefficient way to do things, and I don't think Vbox could handle anything like that anyway (last time I checked you can't even copy & paste between a Vbox OS and a real one). 

I could help you use MIDI natively if you explain the trouble you are having. Explain what your goal and what apps you would like to use. 

I checked the ALSA database and your card appears to be supported. To make sure could you open a terminal, try this command and post the output:
lsusb && aplay -l

---

### Post by EverythingIsNothing on 2010-12-28
Preferably I'd like to have audio output through speakers connected to the controller, as well as MIDI input from a keyboard (output is not really important).  I didn't think the card was supported, and here is the output:

```
user@computer:~$ lsusb && aplay -l
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 004 Device 003: ID 413c:2006 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:1004 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 007: ID 0471:060c Philips (or NXP) Consumer Infrared Transceiver (HP)
Bus 001 Device 006: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 005: ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam
Bus 001 Device 004: ID 0644:8020 TEAC Corp. 
Bus 001 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by EverythingIsNothing on 2010-12-28
So it seems I need to use USB 1.1...

Help :P

---

### Post by cchhrriiss121212 on 2010-12-28
Your card is not shown on the system output you posted so I think it is not supported. The version you have must be different from the one tested on the ALSA page. Not much else you can do with unsupported hardware.

I could recommend a fully functional device if you want to trade this one in.

---

### Post by EverythingIsNothing on 2010-12-28
Well I have that Creative X-Fi you can see there.  I multiboot OSX and Windows and so I have my speakers connected to the Tascam card.  I guess I'll just have to go out and spend the couple bucks on wires :P

Thanks for the help!

---

