---
title: "RME96 and ADA8000"
date: 2011-04-12
forum: Multimedia Software
---

### Post by tom.k.cook on 2011-04-12
I've got an RME96 digital sound card and a Behringer ADA8000 interface AD/DA unit which I am trying to get working with Jack on Ubuntu 10.10.

The unofficial ALSA wiki says I should see two devices for the RME96, but I only see one:

> 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Digi96 [RME Digi96], device 0: Digi96 IEC958 [Digi96 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


If I run amixer, I can set the input connector to the Optical connector:

> 
$ amixer -c 2
Simple mixer control 'Input Connector',0
  Capabilities: enum
  Items: 'Optical' 'Coaxial' 'Internal'
  Item0: 'Optical'
Simple mixer control 'Loopback Input',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Sample Clock Source',0
  Capabilities: enum
  Items: 'AutoSync' 'Internal' 'Word'
  Item0: 'AutoSync'


I've got the ADA8000 set as timing master at 48kHz.

I have .asoundrc configured like this:

> 
pcm.rme_stereo {
    type hw
    card 2
}
ctl.rme_stereo {
    type hw
    card 2
}
pcm.rme_adat {
    type hw 
    card 2
    device 1
}
ctl.rme_adat {
    type hw
    card 2
}


jackd won't start:

> 
$ jackd -R -t 2000 -u -d alsa -d rme_adat -r 48000 -p 256 -n 8 -H -M -i 8 -o 8
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
creating alsa driver ... rme_adat|rme_adat|256|8|48000|8|8|hwmon|hwmeter|-|32bit
Using ALSA driver Digi96 running on card 2 - RME Digi96 at 0xfd000000, irq 16
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server


It's trying to use the right card, but can't open the relevant PCM (I guess because ALSA doesn't report a device 1 on this card).  If I change the .asoundrc to use device 0 then jackd will start, but only with two channels each for capture and playback, and gives lots of errors like this:

> 
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery


I sort of suspect that the problem is that the RME96 is trying to work at 96kHz while the ADA8000 is trying for 48kHz, but I can't figure out how to change this - I sort of thought the jackd command line set that.

Does anyone have this configuration working, or have any suggestions on how to get it to work?  Or perhaps just a suggestion of the right forum to ask questions?

Thanks,
Tom

---

