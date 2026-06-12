---
title: "Asus Xonar D2 problem"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Trollslayer on 2008-07-18
I have an Asus Xonar D2 and the SPDIF output isn't working.
Aplay -l gives:
[COLOR="Blue"]**** List of PLAYBACK Hardware Devices ****
card 0: AV200 [Asus AV200], device 0: Analog [Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AV200 [Asus AV200], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]
Aplay -L gives:
[COLOR="Blue"]default:CARD=AV200
    Asus AV200, Analog
    Default Audio Device
surround40:CARD=AV200,DEV=0
    Asus AV200, Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=AV200,DEV=0
    Asus AV200, Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=AV200,DEV=0
    Asus AV200, Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=AV200,DEV=0
    Asus AV200, Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=AV200,DEV=0
    Asus AV200, Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[/COLOR]
This is Ubuntu 8.04 and ALSA 1.0.17rc2.
Any ideas? :confused:

---

### Post by dmy on 2008-09-08
I had to change the default audio playback device in /etc/asound.conf or ~/.asoundrc:

$ cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
  8: [ 0- 0]: raw midi
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
       ----   ----------------------
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 33:        : timer

$ cat /etc/asound.conf 
pcm.!default {
        type hw
        card 0
        device 1
}

Note that I have a D2X, not DX.

Good luck

---

