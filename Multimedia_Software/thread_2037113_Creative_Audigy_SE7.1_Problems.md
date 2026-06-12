---
title: "Creative Audigy SE7.1 Problems"
date: 2012-08-03
forum: Multimedia Software
---

### Post by jameselliot on 2012-08-03
Sound Card: Creative Audigy SE 7.1 PCI
OS: Ubuntu 12.04

[U]Current situation:
[/U]
With speakers plugged into analog out (blue jack) I get mono sound on left speaker with a lot of white noise.  If I plug speakers into digital out (green jack) I get no sound.


Following problem solutions guide gave:

> james@dino:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> james@dino:~$ lspci -v
07:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs SB0570 [SB Audigy SE]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: snd_ca0106
	Kernel modules: snd-ca0106

_From Alsa website:_
> Sound Blaster Audigy SE
Sound Blaster Audigy Value
Sound Blaster 5.1 VX
	
CA0106
	Details 	[PCI] Not all features on all models supported. On the VX, white noise on playback unless initialized in Windows first. One quirky (but permanent) workaround is to enable the old oss modules, specifically the 100% sound blaster compatible module (sb). You don't have to load the oss modules. The alsa module snd-ca0106 works fine somehow if the old sb module is compiled in the kernel as a module (no white noise). 


> james@dino:~$ sudo modprobe snd-ca0106 
james@dino:~$ 

_Running alsa diagnostics gave:_
[http://jameselliot.co.uk/alsa-info.txt](http://jameselliot.co.uk/alsa-info.txt)

_Alsa mixer looks like:_
[http://jameselliot.co.uk/alsamixer.jpg](http://jameselliot.co.uk/alsamixer.jpg)

Thank you very much for any help you can give me.  I'm looking forward to being able to listen to my tunes again.

---

### Post by jameselliot on 2012-08-05
Can anyone help with this?

I've read lots of other forum posts and nothing has really pointed me to the solution.  Lots of posts suggest disabling IEC958 through alsamixer, I have a checkbox on gnome-alsamixer for IEC958 but I cannot uncheck it.

In alsamixer I have a control for IEC958 which is missing a slider.  It just has a box containing 00.  I've tried selecting this and hitting "M" but this does not unmute it.

I'm confused about ports on my sound card.  Surely the speakers should go into the green port?  Why do I get extremely choppy sound if I plug them into the blue port and no sound if I plug them into the green port?

---

### Post by jameselliot on 2012-08-05
Solved...

Installed kmix.. played around with this... managed to set up analogue output on sound card.

Went back into alsamixer.  Selected the misbehaving IEC958 box, hit "M" and muted the little blighter.

And we have another fix...

:)

---

### Post by jameselliot on 2012-08-05
Okay.. not quite solved...

I rebooted and the sound was broken again. So I had to go back into kmix and do the following steps.

In playback devices mute all except CA0106
In select master channel.. select CA0106
In Audio Setup -> Audio Hardware Setup -> select soundcard CA0106 and set profile to Analogue Stereo Output.

Now I have fantastic sound... but...
I have to do this each time I reboot.  Any idea how I can save these settings?
The volume on the OS taskbar is now set to mute (even with music).  Unmuting this and attempting to use it to control volume does nothing. I have to control volume using kmix. Is it possible to get this volume control to use kmix?

(btw just checked alsamixer and IEC958 isn't muted so this might have been a red herring).

---

