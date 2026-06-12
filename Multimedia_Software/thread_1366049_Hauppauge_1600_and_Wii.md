---
title: "Hauppauge 1600 and Wii"
date: 2009-12-28
forum: Multimedia Software
---

### Post by OhDearAudrey on 2009-12-28
So i have been fooling around with this problem for a few days now. My end goal is to hook my Wii up to my monitor and be able to play it Via a TV Tuner Card. The one i picked up is the hauppauge 1600. I tried TVTime first and it gave me an error: invalid argument CX18 : cannot open capture device dev/video0. The next one i tried was VLC, When i set it to PVR (Which is wrong i think, the Digital half of my card should be DVB) I get a screen of static. Any other configuration gives me usually frequency errors. Next i tried MythTV, i could scan for digital channels, but it didn't find any. When i tried scanning for analog channels, The setup screen closed.

My setup is RCA cables plugged into a coaxial converter box (I know it's bad) from the wii to the back of the Tuner card, i have an analog and a QAM input on the back of the card, what i need to know is: 

A, is this possible, to hook my wii up to a tuner card and be able to play it, streaming.
B, if it is possible, which input do i use (S-video, Analog, QAM)
C, which is the easiest program to use / which will give me the best performance
D, what settings , install, configuration do i use to get it to detect channel 3 (the channel the converter box uses) and let me see the output fromt he wii

Sorry for my poor sentence structure and bad grammar.
I am a total Newbie at linux, literally been using it a week. So any help will be very appreciated.

---

### Post by saedelaere on 2009-12-28
> **OhDearAudrey said:**
> So i have been fooling around with this problem for a few days now. My end goal is to hook my Wii up to my monitor and be able to play it Via a TV Tuner Card. The one i picked up is the hauppauge 1600. I tried TVTime first and it gave me an error: invalid argument CX18 : cannot open capture device dev/video0. The next one i tried was VLC, When i set it to PVR (Which is wrong i think, the Digital half of my card should be DVB) I get a screen of static. Any other configuration gives me usually frequency errors. Next i tried MythTV, i could scan for digital channels, but it didn't find any. When i tried scanning for analog channels, The setup screen closed.

My setup is RCA cables plugged into a coaxial converter box (I know it's bad) from the wii to the back of the Tuner card, i have an analog and a QAM input on the back of the card, what i need to know is: 

A, is this possible, to hook my wii up to a tuner card and be able to play it, streaming.
B, if it is possible, which input do i use (S-video, Analog, QAM)
C, which is the easiest program to use / which will give me the best performance
D, what settings , install, configuration do i use to get it to detect channel 3 (the channel the converter box uses) and let me see the output fromt he wii

Sorry for my poor sentence structure and bad grammar.
I am a total Newbie at linux, literally been using it a week. So any help will be very appreciated.

For analog TV you could also try [TV-Viewer]("http://ubuntuforums.org/showthread.php?t=763698&page=14"), but first of all we should check if your device is set up correctly.

Please open a terminal and run

```
dmesg | grep -i cx18
```

And post the output here.

---

### Post by OhDearAudrey on 2009-12-28
This is the output of ~$ dmesg | grep -i cx18

> [    7.898904] cx18:  Start initialization, version 1.2.0
[    7.898927] cx18-0: Initializing card 0
[    7.898928] cx18-0: Autodetected Hauppauge card
[    7.899156] cx18 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.899722] cx18-0: cx23418 revision 01010000 (B)
[    8.121482] cx18-0: Autodetected Hauppauge HVR-1600
[    8.121483] cx18-0: Simultaneous Digital and Analog TV capture supported
[    8.216604] IRQ 18/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.236693] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[    8.280590] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    8.569035] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[    8.569037] DVB: registering new adapter (cx18)
[    9.031107] cx18-0: DVB Frontend registered
[    9.031109] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[    9.031129] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[    9.031146] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    9.031161] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[    9.031163] cx18-0: Initialized card: Hauppauge HVR-1600
[    9.031178] cx18:  End initialization
[    9.120524] cx18 0000:05:02.0: firmware: requesting v4l-cx23418-cpu.fw
[    9.565904] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[    9.590433] cx18 0000:05:02.0: firmware: requesting v4l-cx23418-apu.fw
[    9.937629] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[    9.943768] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   10.164518] cx18 0000:05:02.0: firmware: requesting v4l-cx23418-cpu.fw
[   10.297989] cx18 0000:05:02.0: firmware: requesting v4l-cx23418-apu.fw
[   10.606166] cx18 0000:05:02.0: firmware: requesting v4l-cx23418-dig.fw
[   10.837116] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   10.856149] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

---

### Post by saedelaere on 2009-12-30
> **OhDearAudrey said:**
> This is the output of ~$ dmesg | grep -i cx18

This is looking good, have you tried TV-Viewer for analog TV?

---

