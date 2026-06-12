---
title: "No Audio - Second Tuner Card"
date: 2009-03-31
forum: Multimedia Software
---

### Post by Nth Degree on 2009-03-31
I recently installed a second capture card (HVR 1600) in to my Myth box, and am running in to an odd problem. The original card was a Hauppauge PVR-350, and it works fine both by itself and with the 1600 in.

The 1600 will work fine by itself, but when both the 350 and 1600 are in, the 1600 will not have any audio. I can hear all of the audio with the 350 feed, but there is zero sound coming from the 1600.

I have done two days of searching trying to find what the problem is. The closest I have come is this email chain: [http://www.spinics.net/lists/linux-dvb/msg27409.html](http://www.spinics.net/lists/linux-dvb/msg27409.html)

This **is not** my log from the v4l2-ctl --log-status, but it is similar enough. One thing to note, when I have both cards in, each card is reported as "CARD #0", not 0 & 1. Could there be some problem w/ cx18 trying to assign both cards to card #0?
```
cx18-0: =================  START STATUS CARD #0  =================
   tveeprom 1-0050: Hauppauge model 74021, rev C1B2, serial# 1441469
   tveeprom 1-0050: MAC address is 00-0D-FE-15-FE-BD
   tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
   tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
   tveeprom 1-0050: audio processor is CX23418 (idx 38)
   tveeprom 1-0050: decoder processor is CX23418 (idx 31)
   tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
   cx18-0: Video signal:              present
   cx18-0: Detected format:           NTSC-M
   cx18-0: Specified standard:        NTSC-M
   cx18-0: Specified video input:     Composite 7
   cx18-0: Specified audioclock freq: 48000 Hz
   cx18-0: Detected audio mode:       mono
   cx18-0: Detected audio standard:   no detected audio standard
   cx18-0: Audio muted:               yes
   cx18-0: Audio microcontroller:     running
   cx18-0: Configured audio standard: automatic detection
   cx18-0: Configured audio system:   BTSC
   cx18-0: Specified audio input:     Tuner (In8)
   cx18-0: Preferred audio mode:      stereo
   cs5345 1-004c: Input:  1
   cs5345 1-004c: Volume: 0 dB
   tuner 2-0061: Tuner mode:      analog TV
   tuner 2-0061: Frequency:       67.25 MHz
   tuner 2-0061: Standard:        0x00001000
   cx18-0: Video Input: Tuner 1
   cx18-0: Audio Input: Tuner 1
   cx18-0: GPIO:  direction 0x00003001, value 0x00003001
   cx18-0: Tuner: TV
   cx18-0: Stream: MPEG-2 Program Stream
   cx18-0: VBI Format: No VBI
   cx18-0: Video:  720x480, 30 fps
   cx18-0: Video:  MPEG-2, 4x3, Variable Bitrate, 6000000, Peak 8000000
   cx18-0: Video:  GOP Size 15, 2 B-Frames, GOP Closure
   cx18-0: Audio:  48 kHz, Layer II, 224 kbps, Stereo, No Emphasis, No CRC
   cx18-0: Spatial Filter:  Manual, Luma 1D Horizontal, Chroma 1D Horizontal, 0
   cx18-0: Temporal Filter: Manual, 8
   cx18-0: Median Filter:   Off, Luma [0, 255], Chroma [0, 255]
   cx18-0: Status flags: 0x00200001
   cx18-0: Stream encoder MPEG: status 0x0000, 0% of 2016 KiB (63
buffers) in use
   cx18-0: Stream encoder YUV: status 0x0000, 0% of 2048 KiB (16 buffers) in use
   cx18-0: Stream encoder PCM audio: status 0x0000, 0% of 1008 KiB (63
buffers) in use
   cx18-0: Read MPEG/VBI: 5240832/0 bytes
   cx18-0: ==================  END STATUS CARD #0  ==================

```

I was going to follow the support in that email chain, but since the audio works when the HVR-1600 is in by itself, I was not sure if it would it. 


If anyone has ideas on what I need to do to fix this, I would really appreciate the help. If this is in the wrong section (or the wrong board for help), let me know where I need to head. Also, please spell out any instructions, as I am still trying to learn how to work in linux. 

Thanks in advance.

---

