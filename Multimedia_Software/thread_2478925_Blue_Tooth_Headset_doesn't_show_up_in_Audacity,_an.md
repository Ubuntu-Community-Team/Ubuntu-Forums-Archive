---
title: "Blue Tooth Headset doesn't show up in Audacity, and typical advice won't work"
date: 2022-09-08
forum: Multimedia Software
---

### Post by RangerK on 2022-09-08
All of the content I've found about this problems says to just re-scan audio devices, or restart Audacity with devices ready.  But neither of those work, so I thought I'd ask here.

I know that my headphones are working because I can play Youtube videos and hear them.  In the Pulse Audio Volume Controls, they appear as **"JBL TUNE710BT"  Port: Headset.**

[B]Linux version:
[/B]
NAME="Ubuntu"
VERSION="20.04.5 LTS (Focal Fossa)"

[B]The options I see in Audacity:
[/B]
ATR USB microphone: Audio (hw:1,0)
HDA Intel PCH: ALC294 Analog (hw:2,0)
HDA Intel PCH: HDMI 0 (hw:2,3)
HDA Intel PCH: HDMI 1 (hw:2,7)
HDA Intel PCH: HDMI 2 (hw:2,8)
HDA Intel PCH: HDMI 3 (hw:2,9)
HDA Intel PCH: HDMI 4 (hw:2,10)

**Result of command **```
aplay --list-devices
```

```
**** List of PLAYBACK Hardware Devices ****
card 1: microphone [ATR USB microphone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My work would be much better if I could listen to the audio in my headphones instead of through my laptop speakers.  Any advice for troubleshooting is greatly appreciated.  Thanks!

---

### Post by tea for one on 2022-09-09
> **RangerK said:**
> 
[B]The options I see in Audacity:
[/B]
ATR USB microphone: Audio (hw:1,0)
HDA Intel PCH: ALC294 Analog (hw:2,0)
HDA Intel PCH: HDMI 0 (hw:2,3)
HDA Intel PCH: HDMI 1 (hw:2,7)
HDA Intel PCH: HDMI 2 (hw:2,8)
HDA Intel PCH: HDMI 3 (hw:2,9)
HDA Intel PCH: HDMI 4 (hw:2,10)

Are these options via Audacity > Preferences > Devices > Playback?
Can you search (scroll down) these options to see if you have [COLOR="#0000FF"]default[/COLOR]?

---

