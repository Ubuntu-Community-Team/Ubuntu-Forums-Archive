---
title: "Audio going through wrong HDMI port"
date: 2010-01-11
forum: Multimedia Software
---

### Post by azazel00 on 2010-01-11
Hi there,

I've got an Acer AX3200 desktop computer which is being reassigned to HTPC duties. It has two VGAs (Hybrid SLI): 9300 GE and 8200. The 8200 is being detected as a 9200 by XBMC (whatever that means).

Note: I obviously dont expect Hybrid SLI to work on Linux.

```
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1)

```

I've managed to get video working through both HDMI ports. However, Audio will only go out the integrated port (8200/9200). I'd like to use the dedicated (9300) card primarily, having both video and audio outputted through it.

Is there any way I can force alsa to use that device in partticular? .asoundrc?? How can I determine which device to assign the audio to?

thanks,
az

---

