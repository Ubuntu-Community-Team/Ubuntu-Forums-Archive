---
title: "Another cry for help with HDMI audio"
date: 2010-12-06
forum: Multimedia Software
---

### Post by GuiGuy on 2010-12-06
Guys,
It's been a trying time. My media box's motherboard went down for the count. Right in the middle of an upgrade :(

I have it back, but no sound over HDMI

>  sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


gstreamer-properties has the ALSA plugin and Device as ATI HDMI for output. It lets me play an audible test sound.

VLC is, of course, working OK as well, so I can presume that the hardware is OK and capable.

No other sound based applications, including mythtv, work. The silence is deafening. 

Q: What should my sound options in the MythTV frontend be set to? Or should I give up? ;)

TIA

---

### Post by efflandt on 2010-12-06
I am just guessing because I have nvidia.  But assuming that the following works:

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```You might try adding a line to /etc/pulse/default.pa to tell it about your HDMI sound:

```
#load-module module-alsa-sink (after this line)
**load-module module-alsa-sink device=hw:1,3**
```Reboot, tune Rythmbox to an internet radio station (or other music you have), then try different Output devices in Sound Preferences to see if one of them works for HDMI audio.

Note, for my nvidia it is NOT the one that says "HDA NVidia Digital Stereo (HDMI)", I get HDMI sound from the one that simply says "HDA NVidia".  So don't go by what it says, go by whatever in the Output tab works for Rythmbox or other gui sound player.

---

