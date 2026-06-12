---
title: "Hauppauge 1600 no audio/sound"
date: 2012-10-15
forum: Multimedia Software
---

### Post by kyle12345 on 2012-10-15
I have search for the last day to try to get my second Hauppauge 1600 audio working.  This is what happen... I replace my Hauppauge 150 with a Hauppauge 1600.  I already had a Hauppauge 1600 in my mythtv-backend. 
The 1st Hauppauge 1600 has video and sound.
The 2nd (new) Hauppauge 1600 has video but no sound
I found many solutions stating that:
MythTV backend->Utilities/Setup -> TV Setting -> Recording Profiles -> MPEG-2 Encoders (PVR-x50, PVR-500)) to change them all to 48kHz with a bitrate of 224kb/s.
would fix the audio problem but it did not for me.

I have tried to compile the lastest ittv drivers, but this did not help.

??????What else should I try??????
---------INFO------------
00:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip
MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. WinTV HVR-1600
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at c4000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
        Kernel driver in use: cx18
        Kernel modules: cx18

00:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
        Subsystem: Hauppauge computer works Inc. Device 740c
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at c8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
        Kernel driver in use: cx18
        Kernel modules: cx18

root@karm-K8Upgrade-VM800:~# dmesg | grep cx-18
root@karm-K8Upgrade-VM800:~# dmesg | grep cx18
[   13.580191] cx18:  Start initialization, version 1.5.1
[   13.585542] cx18-0: Initializing card 0
[   13.585549] cx18-0: Autodetected Hauppauge card
[   13.585622] cx18 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.585633] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   13.594145] cx18-0: cx23418 revision 01010000 (B)
[   13.984182] cx18-0: Autodetected Hauppauge HVR-1600
[   13.984185] cx18-0: Simultaneous Digital and Analog TV capture supported
[   14.871615] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   15.139559] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   15.139565] DVB: registering new adapter (cx18)
[   15.585797] cx18 0000:00:09.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   15.586180] cx18-0: DVB Frontend registered
[   15.586185] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   15.586295] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   15.586518] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   15.586676] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   15.586680] cx18-0: Initialized card: Hauppauge HVR-1600
[   15.599192] cx18-1: Initializing card 1
[   15.599198] cx18-1: Autodetected Hauppauge card
[   15.599275] cx18 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.599285] cx18-1: Unreasonably low latency timer, setting to 64 (was 32)
[   15.613897] cx18-1: cx23418 revision 01010000 (B)
[   15.836729] cx18-1: Autodetected Hauppauge HVR-1600
[   15.924078] cx18-1: Simultaneous Digital and Analog TV capture supported
[   16.086138] cs5345 3-004c: chip found @ 0x98 (cx18 i2c driver #1-0)
[   39.406606] cx18-1: Registered device video1 for encoder MPEG (64 x 32.00 kB)
[   39.406612] DVB: registering new adapter (cx18)
[   39.539628] cx18-1: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   39.827875] cx18-1: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   39.918455] cx18-1: FW version: 0.0.74.0 (Release 2007/03/12)
[   40.031781] cx18 0000:00:0a.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   40.039903] cx18-1: DVB Frontend registered
[   40.039909] cx18-1: Registered DVB adapter1 for TS (32 x 32.00 kB)
[   40.040494] cx18-1: Registered device video33 for encoder YUV (20 x 101.25 kB)
[   40.040693] cx18-1: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   40.040816] cx18-1: Registered device video25 for encoder PCM audio (256 x 4.00 kB)
[   40.040820] cx18-1: Initialized card: Hauppauge HVR-1600
[   40.051120] cx18:  End initialization
[   40.241723] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   40.383070] cx18-alsa: module loading...
[   40.504171] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   40.632051] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   41.023638] cx18-1 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   41.041838] cx18-1 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   41.736878] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   41.755025] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

---

