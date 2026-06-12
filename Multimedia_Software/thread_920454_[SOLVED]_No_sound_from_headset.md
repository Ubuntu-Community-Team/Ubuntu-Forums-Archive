---
title: "[SOLVED] No sound from headset"
date: 2008-09-15
forum: Multimedia Software
---

### Post by Benjaminp on 2008-09-15
I have sound from my speakers (although theres alot of static), and absolutely no sound from my headphones. I've tried removing pulseaudio and installing esound (from [http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)). Is there anything else I can do to get my headphones to work?
Here's a bit of info:
benjamin@benjamin:~$ lspci |grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
benjamin@benjamin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Am I doing something wrong, or is there a bug with my headphones?


Update:
when I open the sound preferences, and change "Sound playback" from autodetect to USB Audio, it gives this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

---

### Post by Benjaminp on 2008-09-15
Bump

---

### Post by Benjaminp on 2008-09-15
Actually I just got it to work!! 

Anyone who has this problem might find this useful:

I switched the headphones to a different USB port, and that added a device in the sound device list called 'default.' I then installed asoundconfig-gtk
and set my device to 'default'.

---

