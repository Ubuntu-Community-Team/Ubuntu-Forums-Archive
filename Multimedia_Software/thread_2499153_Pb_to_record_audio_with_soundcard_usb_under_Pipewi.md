---
title: "Pb to record audio with soundcard usb under Pipewire"
date: 2024-07-15
forum: Multimedia Software
---

### Post by LeSanglier on 2024-07-15
Hello,

I am under Ubuntu 24.04 and I have a soundcard usb:C-Media Electronics,  Inc. Audio Adapter (Unitek Y-247A).
Do you have tips to record audio  with the audio-in Jack? 
I would like to use the****qpwgraph.

```
util01@station54:~$ wpctl status
PipeWire 'pipewire-0' [1.0.5, util01@station54, cookie:534854888]
 &#9492;&#9472; Clients:
        32. pipewire                            [1.0.5, util01@station54, pid:1409]
        34. WirePlumber                         [1.0.5, util01@station54, pid:1406]
        35. WirePlumber [export]                [1.0.5, util01@station54, pid:1406]
        59. lxqt-volume                         [1.0.5, util01@station54, pid:1797]
        60. wpctl                               [1.0.5, util01@station54, pid:2027]

Audio
 &#9500;&#9472; Devices:
 &#9474;      46. Built-in Audio                      [alsa]
 &#9474;      47. Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM] [alsa]
 &#9474;      48. Audio Adapter (Unitek Y-247A)       [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      33. Audio Adapter (Unitek Y-247A) Analog Stereo [vol: 0.40]
 &#9474;  *   49. Built-in Audio Analog Stereo        [vol: 0.51]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   42. Audio Adapter (Unitek Y-247A) Mono  [vol: 1.10]
 &#9474;      50. Built-in Audio Analog Stereo        [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         1. Audio/Source  alsa_input.usb-C-Media_Electronics_Inc._USB_Audio_Device-00.mono-fallback

```

```
util01@station54:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 1c4f:0034 SiGma Micro XM102K Optical Wheel Mouse
Bus 002 Device 004: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0d8c:0014 C-Media Electronics, Inc. Audio Adapter (Unitek Y-247A)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

Thanks you! :D

---

### Post by bobunderwood99 on 2024-07-15
Use Audacity to record your audio.

You probably don't need qpwgraph (or helvium, a GTK option) to make it work - just install pavucontrol instead (which also gives you access to the Pro Audio profile).

---

### Post by tea for one on 2024-07-16
Sound ;) advice from bobunderwood99
Audacity and pavucontrol (recording tab) is a perfect combination.

If you want a different approach, try this:-

Open firefox and listen to some audio
Identify sound source with pipewire
```
redact@k2:~$ pw-cli list-objects | grep node.name
 		node.name = "Dummy-Driver"
 		node.name = "Freewheel-Driver"
 		node.name = "Midi-Bridge"
 		node.name = "alsa_input.pci-0000_74_00.6.analog-stereo"
 		node.name = "alsa_output.pci-0000_74_00.1.hdmi-stereo"
 		node.name = "Firefox"
```
Record sound source e.g.
```
redact@k2:~$ pw-record --target "Firefox" recording.mp3
```

---

