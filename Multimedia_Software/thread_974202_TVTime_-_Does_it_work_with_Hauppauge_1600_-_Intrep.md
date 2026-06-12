---
title: "TVTime - Does it work with Hauppauge 1600 - Intrepid?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by sofasurfer on 2008-11-07
When I start it up I get the message "CX18: Invalid argument - Cannot open capture device /dev/video0".

I think this means it won't work using the cx18 driver. Is there a quick fix or not?

---

### Post by cariboo on 2008-11-07
What is the output od **dmesg** when you load the module for you TV card. To see the output of dmesg open a terminal and type:

```
dmesg
```

I think you have to add card and tuner parameters when you insert the module.

Jim

---

### Post by sofasurfer on 2008-11-07
Heres my dmesg output. I know my cards working right because I am able to use mplayer and VLC to view tv.

```

daryl@daryl-desktop:~$ dmesg | grep cx18
[   11.500188] cx18:  Start initialization, version 1.0.0
[   11.500228] cx18-0: Initializing card #0
[   11.500231] cx18-0: Autodetected Hauppauge card
[   11.500601] cx18 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.500609] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   11.502501] cx18-0: cx23418 revision 01010000 (B)
[   11.702477] cx18-0: Autodetected Hauppauge HVR-1600
[   11.702479] cx18-0: VBI is not yet supported
[   11.968209] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   11.968229] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.486554] cx18-0: Disabled encoder IDX device
[   12.486689] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   12.486693] DVB: registering new adapter (cx18)
[   12.651802] cx18-0: DVB Frontend registered
[   12.651835] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   12.651866] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   12.651870] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   12.651974] cx18:  End initialization
[   19.163459] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   19.722868] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.729236] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   20.921504] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)


```

---

### Post by gusman21 on 2008-11-20
Please see this post:

[http://www.opensubscriber.com/message/ivtv-users@ivtvdriver.org/8374223.html](http://www.opensubscriber.com/message/ivtv-users@ivtvdriver.org/8374223.html)

---

### Post by saedelaere on 2008-11-21
Did anyone try to use [TV-Viewer]("http://ubuntuforums.org/showthread.php?t=763698")?

I think analogue TV should work with the latest beta. But I can't check myself.

---

