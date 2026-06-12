---
title: "Nvidia ION 5.1 audio jacks only giving stereo"
date: 2011-05-10
forum: Multimedia Software
---

### Post by solitaire on 2011-05-10
I've a Nvidia ION board (Zotec IONITX-F-E)

In XP the 3 audio jacks work fine giving me 5.1 sound when i use my 5.1 headset.

But in Ubuntu 10.10 i only get left & right outputs.

"aplay -Ll"
```

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

``````

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
alsamixer settings:```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                                                                                                                                  F1:  Help               &#9474;
&#9474; Chip: Nvidia MCP79/7A HDMI                                                                                                                                        F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                                                                                          F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -28.00]                                                                                                                                    Esc: Exit               &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;         &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;&#9618;&#9618;&#9474;           &#9474;  &#9474;                                                      &#9474;
&#9474;         &#9500;&#9472;&#9472;&#9508;           &#9500;&#9472;&#9472;&#9508;           &#9492;&#9472;&#9472;&#9496;           &#9500;&#9472;&#9472;&#9508;           &#9500;&#9472;&#9472;&#9508;           &#9492;&#9472;&#9472;&#9496;           &#9500;&#9472;&#9472;&#9508;           &#9500;&#9472;&#9472;&#9508;           &#9492;&#9472;&#9472;&#9496;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;           &#9484;&#9472;&#9472;&#9488;         &#9474;
&#9474;         &#9474;OO&#9474;           &#9474;OO&#9474;                          &#9474;OO&#9474;           &#9474;MM&#9474;                          &#9474;OO&#9474;           &#9474;MM&#9474;                          &#9474;OO&#9474;           &#9474;OO&#9474;           &#9474;OO&#9474;         &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9496;           &#9492;&#9472;&#9472;&#9496;                          &#9492;&#9472;&#9472;&#9496;           &#9492;&#9472;&#9472;&#9496;                          &#9492;&#9472;&#9472;&#9496;           &#9492;&#9472;&#9472;&#9496;                          &#9492;&#9472;&#9472;&#9496;           &#9492;&#9472;&#9472;&#9496;           &#9492;&#9472;&#9472;&#9496;         &#9474;
&#9474;          56          100<>100        99<>99        100<>100         6<>6           0<>0          10<>10         10<>10          0<>0                                                      &#9474;
&#9474;   <    Master    >  Headphone         PCM           Front        Front Mic    Front Mic Boos      Line           Mic         Mic Boost        S/PDIF     S/PDIF Default    S/PDIF 1       &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                                                                           &#9474;
&#9474;                                                                                                                                  
```

Anyone got any ideas how to get 5.1 sound working from the rear jacks?

if you need more info please ask...

---

### Post by lidex on 2011-05-11
First try adding a model quirk to alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-6ch-dig 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

No joy? Change model to '3stack-6ch'

---

### Post by solitaire on 2011-05-12
> **lidex said:**
> First try adding a model quirk to alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-6ch-dig 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

No joy? Change model to '3stack-6ch'


Many Thanks!!!!!
Added the line to alsa-base.conf
Rebooted
Now in alsamixer there's a new option "Channel Mode" changed that from "2ch" to "6ch"
Now sound through all speakers!!!

Finally working...

Off to watch Kick-*** in 5.1 surround sound ^_^

---

