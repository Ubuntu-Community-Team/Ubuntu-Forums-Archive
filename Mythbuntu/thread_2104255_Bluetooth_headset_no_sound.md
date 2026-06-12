---
title: "Bluetooth headset no sound"
date: 2013-01-12
forum: Mythbuntu
---

### Post by DrJohn999 on 2013-01-12
Mythbuntu 12.04 / 0.25.2.15 on Dell D610 laptop. In addition to Mtyhbuntu, installed bluez, blueman, xfce-4-mixer. Discover, add, and pair to Motorola S305 phones (which work fine with Ubuntu 12.04 on another laptop). Connect to Audio Sink and to Headset services; no headset devices appear in MythTV or in VLCPlayer. Headset device not apparently present:
```
~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=ICH6
    Intel ICH6, Intel ICH6
    Default Audio Device
sysdefault:CARD=ICH6
    Intel ICH6, Intel ICH6
    Default Audio Device
front:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Front speakers
surround40:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Direct sample mixing device
dmix:CARD=ICH6,DEV=4
    Intel ICH6, Intel ICH6 - IEC958
    Direct sample mixing device
dsnoop:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Direct sample snooping device
dsnoop:CARD=ICH6,DEV=4
    Intel ICH6, Intel ICH6 - IEC958
    Direct sample snooping device
hw:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Direct hardware device without any conversions
hw:CARD=ICH6,DEV=4
    Intel ICH6, Intel ICH6 - IEC958
    Direct hardware device without any conversions
plughw:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Hardware device with all software conversions
plughw:CARD=ICH6,DEV=4
    Intel ICH6, Intel ICH6 - IEC958
    Hardware device with all software conversions
```

```
dmesg
...
[   90.892062] input: 00:0D:FD:36:CA:1E as /devices/virtual/input/input7
...
```
(above is the mac address of the phones). 

Looks as if the mic in the phones is detected, but not the output to the phones.

Alsa-mixer shows only the Intel ICH6 audio devices. The "Phone" device volume isn Alsa-mixer does nothing on the BT phones. Same behavior for Nokia BH-905i.

The built-in BT adapter in the Dell D610 worked when Ubuntu 12.04 was installed, and in this Mythbuntu install it works fine with a BT mouse, so no apparent h/w problems there.

In Myth, none of the selectable audio devices (Setup, Audio, ...) cause output through the phones.

Pulseaudio pckg was not installed by Mythbuntu, should it or others be?

---

### Post by nickrout on 2013-01-13
try installing bluez-audio. Avoid pulse if possible.

---

### Post by DrJohn999 on 2013-01-14
bluez-audio makes no difference. I briefly installed pulse, but this old laptop doesn't support it well and the sound breaks up. 

The headset is visible to hcitool, as is the mouse. The problem I'm having is there is no obvious way to redirect sound output to bluetooth, in contrast to Settings, Sound... on a main 12.04 installation. And yes, this works just fine with these phones from my desktop of that flavor.

I considered trying to hook the bluetooth phones up directly by manually configuring alsa, but that's not the point as I'll want to select which output.

So, for xfce, where is the equivalent of Settings, Sound??

---

