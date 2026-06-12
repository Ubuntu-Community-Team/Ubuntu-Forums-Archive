---
title: "Video stalls computer"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by revslowmo on 2007-05-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/99867](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/99867) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a strange problem, that I have no idea what todo with. I am running ubuntu 7.04 and when I try to play a video file of the resolution below the system turns the video screen green then locks the system up. I have tried reencoding it with ffmpeg and if I keep the resolution the same but change the codec I have the same problem, however if I change the resolution and keep the codec the same it doesnt lock up. I am using the savage video drivers, however when I use the default vesa drivers it doesnt stall but the video plays too slow on my laptop. Any ideas where I should go next.

RIFF (little-endian) data, AVI, 576 x 240, 23.98 fps, video: DivX 5, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

lspci -v output 
01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 0020
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        Memory at 90000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at 98000000 [disabled] [size=64K]

---

### Post by revslowmo on 2007-05-17
No help on this one?

---

