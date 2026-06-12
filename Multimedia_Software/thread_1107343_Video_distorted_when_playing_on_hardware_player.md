---
title: "Video distorted when playing on hardware player"
date: 2009-03-26
forum: Multimedia Software
---

### Post by micxer on 2009-03-26
I transcoded a DVD into H.264 using Handbrake. The problem now is that the video looks distorted when it's played on my Popcorn Hour. What I don't understand is, that it seems to honour the aspect ratio in other files. "MP4Box -info" list this for my encoded file:

```
* Movie Info *
	Timescale 600 - Duration 01:56:25.450
	Fragmented File no - 3 track(s)
	File Brand isom - version 1
	Created: GMT Wed Mar 25 22:47:48 2009

File has root IOD
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 2 (0x29)
No streams included in root OD

Track # 1 Info - TrackID 1 - TimeScale 48000 - Duration 01:56:25.440
Media Info: Language "Undetermined" - Type "vide:avc1" - 174636 samples
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 704 x 416 - Profile High @ Level 3
NAL Unit length bits: 32
Pixel Aspect Ratio 125:88 - Indicated track size 1000 x 416
Self-synchronized
```

This one looks distorted. The other one that looks fine, has the following data:

```
* Movie Info *
	Timescale 600 - Duration 01:15:10.720
	Fragmented File no - 2 track(s)
	File Brand isom - version 1
	Created: GMT Wed Jan  7 16:06:22 2009

File has root IOD
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 1 (0x28)
No streams included in root OD

Track # 1 Info - TrackID 1 - TimeScale 25000 - Duration 01:15:10.640
Media Info: Language "Undetermined" - Type "vide:avc1" - 112766 samples
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 704 x 544 - Profile High @ Level 5.1
NAL Unit length bits: 32
Pixel Aspect Ratio 16:11 - Indicated track size 1024 x 544
Self-synchronized
```

Anybody any idea why this happens? I mean, both have an aspect ratio set, but one looks ok and one looks distorted. Thanks for any advice.

---

### Post by micxer on 2009-03-27
Ok, I should know how to use my own devices :-) Just found the setting to change the format so that it looks ok.

:popcorn:

---

