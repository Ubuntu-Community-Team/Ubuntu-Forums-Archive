---
title: "Audio over HDMI"
date: 2011-02-27
forum: Multimedia Software
---

### Post by boyoM3 on 2011-02-27
Please please please can someone help me work out why sound isn't working over HDMI?

I have a Zotac H55 ITX board and have upgraded the BIOS o the latest level so the HDA controller and internal HDMI are available. 

In dmesg during boot it sees the sound chip as ALC880 and if i run sound properties the card appears. Hardware tab shows the card and Digital Stereo (HDMI Output) is selected in the settings drop down box.

All channels are unmuted in aplay.

When i run gstreamer properties the defaut output is set to:-

Plugin: ALSA
Device: Intel HDMI 1

When i test - nothing! 

Can someone talk me through the troubleshooting process?

Cheers,

Warren

---

### Post by boyoM3 on 2011-02-27
Output from DMESG;-

[   14.576859] hda_codec: ALC888: BIOS auto-probing.
[   14.622460] HDMI: detected monitor  at connection type HDMI
[   14.622462] HDMI: available speakers: FL/FR
[   14.622466] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16

Output from aplay -i;-

card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I get no sound at all.. Ive tried HDMI to my Sony HTSF1100 and my Samsung TV but neither work.

Cheers,

Warren

---

