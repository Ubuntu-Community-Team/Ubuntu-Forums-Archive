---
title: "Intel 82801JI (ICH10 Family) Audio Stopped Working"
date: 2009-05-01
forum: Multimedia Software
---

### Post by user2037 on 2009-05-01
After the upgrade to 9.04 the sound worked if I moved to the green audio out jack (from the black). However, recently audio stopped working again and ALSA seems unaware of my card now.

"aplay -l" says: "aplay: device_list:217: no soundcards found..."

And "/proc" has no "/asound" folder.

"lsmod | grep snd" is also empty.

"lspci -v" produces:
```

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8346
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>

```

Recently I did install a Conexant HSF modem driver from Linuxant. Perhaps it caused a conflict of some kind. I have removed the driver, but still there is no audio love.

EDIT: Ubuntu 9.04 Live CD does have working audio with my hardware arrangement. So it appears the Linuxant driver must be to blame.

EDIT: Solved by installing reinstalling Linuxant's modem driver then installing their ALSA driver from "http://www.linuxant.com/alsa-driver/". Now the modem and audio both work.

EDIT: After restarting ALSA doesn't work. Changing the playback device to OSS works for some applications, but it cuts out when some apps try to play sounds. I suspect the troublesome apps are using ALSA despite my preference for OSS. They include Firefox, Thunderbird, and the modem. This is frustrating.

EDIT: Linuxant tech support said their ALSA driver was unnecessary so I removed it. Sound worked again when the device was changed to "HDA Intel... (ALSA)". However, after awakening from Hibernation the sound test produces the error: "audiotestsrc wave=sine... Could not open audio device for playback".

---

