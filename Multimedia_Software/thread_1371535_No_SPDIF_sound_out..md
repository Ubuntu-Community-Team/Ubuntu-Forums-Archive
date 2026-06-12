---
title: "No SPDIF sound out."
date: 2010-01-03
forum: Multimedia Software
---

### Post by suhewabe on 2010-01-03
Here's my information: 

I have an Asus m3n78-vm motherboard, and I installed 9.10 64-bit.  I'm trying to get the sound to come out of the optical out.  It was working when it was a Windows Vista Home box.

> lspci -v
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 8345
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at f8e78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


>  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server


I made sure that in alsamixer I turned off mute for all playback devices - IEC958's too.

I notice that in the "aplay -L" at the end it says "Playback/recording through the PulseAudio sound server".  I read several posts that talked about disabling PulseAudio, but I think they were old posts and I don't know if that still applies.  If it does how do I disable it?  If not, does anyone have a possible solution or some more debugging suggestions?

Thanks in advance.

---

### Post by suhewabe on 2010-01-04
bump.  Posts get lost fast!

---

### Post by suhewabe on 2010-01-04
Ok - getting tired of trying things and failing.  I don't like it, but I might have to put Windows back on.  :(

---

### Post by cajual on 2010-01-05
The second, indented line in **aplay -L** merely *explains* the option.  Pulse is just one of the options available.

---

### Post by Namikon on 2010-01-06
I have the same problem. Same Mainboard (m3n78-vm), same lspci /  			 				 aplay -l /  			 				 aplay -L outputs, and installed Ubuntu 9.10 x64.

Tried with gnome-alsa mixer but no success. there's no sound over optical out.


Any ideas on that yet?

---

