---
title: "no sound with realtek sound card"
date: 2010-06-06
forum: Multimedia Software
---

### Post by NickJones0 on 2010-06-06
Hi
It'd be great if someone had time to help me. I want to use Blender on Ubuntu because it always crashes on Windows but I can't get any sound out of Ubuntu (or Puppy Linux which I also use).
There is no sound output at all - no beeps, no ogg audio, no sound from video. Alsamixer all parts are unmuted.
I can record OK and when I play back recordings I see the VU peak meter moving.
Sound is fine with windows.
I've worked through this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and many other pieces of advice on forums.
I tried to install Realtek drivers but I had to complile them and got confused.
I can use the terminal but don't really understand more complex operations.

My latest info from ALSA is here. It's pretty long so I didn't paste it all.
 [http://www.alsa-project.org/db/?f=ae93b2e34a29902be4bd27d9c57b4e1a3de1469b](http://www.alsa-project.org/db/?f=ae93b2e34a29902be4bd27d9c57b4e1a3de1469b)


Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel

according to mobo manual:
chipset:nVIDIA Ge Force 6100/nForce 405
audio: realtek ALC883  codec chip

List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help appreciated. I'm happy to go off and learn how to compile drivers but I feel I'm just throwing random bits of code at the computer and hoping it will work.

Nick

---

