---
title: "Can the automatic audio sample rate conversion be suppressed ?"
date: 2009-02-22
forum: Multimedia Software
---

### Post by bwiberg on 2009-02-22
First: I have already done extensive search through various forums and sites and tried several suggestions. Actually also found a way to do what I want. But only partly...

Problem: Recently bought a USB DAC converter and now wants to stream bit perfect audio to this device with no interference from soundcard or whatever. In this context: NO conversion of sample rate of music source!

Playing through Rhythmbox or Movie Player to the USB-DAC ALWAYS outputs sample rate 48000, so the common CD's with sample rate 44100 is always converted to 48000 first.

Only way I have found to prevent this is using the Pulse Audio Devics Chooser. When I move the stream in PulseAudio Volume Control to the USB DAC I now ALWAYS get sample rate 44100. So basically same problem, just another sample rate. I noted that the Pulse Audio Manager -> Server information -> Default sample type: says "s16le 2ch 44100Hz". Maybe that's the cause?

The only way I have found to play music unaltered is using the line command player 'aplay' using a command like this:

aplay -D plughw:1,0 *.wav

This will play the wav files through the USB DAC unaltered just like I want. But I really would like to use a GUI like Rhythmbox for my playback.

Various specs:

I'm on Ubuntu 8.04, soundcard is onboard Realtek ALC 883.

Output from cat /proc/asound/modules:
 0 snd_hda_intel
 1 snd_usb_audio

Output from cat /proc/asound/cards:
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfb100000 irq 21
 1 [default        ]: USB-Audio - C-Media USB Headphone Set  
                      C-Media USB Headphone Set   at usb-0000:00:02.0-2, full speed

Output from aplay -lL:
default:CARD=NVidia
    HDA NVidia, ALC883 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Hope I make sense - any input greatly appreciated

---

