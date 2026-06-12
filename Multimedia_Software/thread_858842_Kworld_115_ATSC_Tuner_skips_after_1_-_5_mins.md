---
title: "Kworld 115 ATSC Tuner skips after 1 - 5 mins"
date: 2008-07-14
forum: Multimedia Software
---

### Post by bowsercake on 2008-07-14
I am running a KWorld 115 Digital TV tuner on a board with ATI 3200 HD integrated graphics.  I am using Me-TV to watch TV and my channels.conf is set up properly and works.  I can tune to most channels fine with my reception. Most channels are clear and hardly ever skip from poor reception. However, after a few minutes the video will start skipping, maybe once, and then faster and faster until it skips one second and then plays one second. This skipping will continue until the channel is changed.  Once it is changed (and possibly changed back) the video will be clear and won't skip again.  But, after 5 minutes or so it will begin skipping again until the channel has been changed once more.

I believe my Graphics are working properly. So I don't think that is the problem.
fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

```

I have also set up my tuner based on the MythTV wiki and posts here.  I believe that this output is correct
dmesg:
```

[   39.909919] tuner 1-0061: chip found @ 0xc2 (saa7133[0])
[   39.909944] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   39.909947] tuner 1-0061: type set to Philips TUV1236D AT
[   39.909949] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   39.909951] tuner 1-0061: type set to Philips TUV1236D AT
[   39.911742] saa7133[0]: registered device video0 [v4l2]
[   39.911758] saa7133[0]: registered device vbi0
[   39.958813] saa7134 ALSA driver for DMA sound loaded
[   39.958838] saa7133[0]/alsa: saa7133[0] at 0xfbfff800 irq 21 registered as card -2
[   40.037858] nxt200x: NXT2004 Detected
[   40.054013] DVB: registering new adapter (saa7133[0])
[   40.054017] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   40.061734] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   40.475821] nxt2004: Waiting for firmware upload(2)...
[   40.762281] lp0: using parport0 (interrupt-driven).
[   42.014569] nxt2004: Firmware upload complete


```

This also seems to show that the tv tuner has loaded properly.
lspci -v:
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fbc00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

03:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Unknown device 7352
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at fbfff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>


```

I have added the correct modules for the KWorld 115 to /etc/modules
/etc/modules:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
saa7134
saa7134-dvb

```

When running Me-TV through the console I do not see any errors.  The skipping is also shown in the recordings so I do not think it is a video issue with the ATI drivers. I think it is related to the KWorld TV Tuner drivers or maybe it is even a hardware issue.  However, I can't find anyone else who has the same problem that I do.  Doesn't seem to be a Me-TV problem.

What could cause this skipping? Has anyone else had the same problem and fixed it? Thanks guys.

---

### Post by bowsercake on 2008-07-14
well, I tried to play the digital TV through mplayer using 'mplayer dvb:///' and I was able to reproduce the error.  The video will play fine but after 5 minutes or so the video will start to skip continuously until the channel changes.

Mplayer gives me an error about the video buffer being full.  I assume that the same thing is happening in Me-TV.

However, Me-TV has a xine configuration file, "~/me-tv/xine.config". The default values are
```
.version:2
engine.buffers.audio_num_buffers:50
engine.buffers.video_num_buffers:1000
```

I have increase the video num buffers number but it still seems to skip.  When i moved the numbers down the audio would not play at all.

---

