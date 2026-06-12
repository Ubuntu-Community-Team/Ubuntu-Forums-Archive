---
title: "Problem playing TS file encoded in &quot;HD-DVD.REMUX.1080P.H264.DDPlus.DD51.DC&quot;"
date: 2012-01-22
forum: Multimedia Software
---

### Post by mrsah on 2012-01-22
If played with *SMPlayer*, both video and audio seems good, except the video seems to be running a little bit faster than it should be (hardly noticeable) and the video and the audio can not get synchronized.

Tried *Audio/video auto synchronization*, *A-V sync correction*, manually set audio delay, no luck. Tried other Video decoders like *ffh264* & *ffh264crystalhd*, other demuxers like *rawvideo* & *lavf*, still no luck. Tried switching on/off *Software video equalizer*, *Direct rendering*, *Draw video using slices*, *Allow frame drop*, none of them helps.

If played with *Movie Player*, it says "required software to play this file is not installed" and then fails searching for plugin "*audio/x-eac3 decoder*". If continue playing, there is sound at the beginning but in very bad quality, and then it goes mute. Fast-forward button is disabled, clicking on progress bar freezes the playing.

[B]Now does anyone know how get SMPlayer to play a video file in such format? Or is there a eac3 audio decoder for Movie Player that I could try?
[/B]

The Ubuntu version is 11.10, fully updated.

The video file is of "ts" format. And in the Properties dialog:
[INDENT]Type: MPEG-2 transport stream (video/mp2t)
**Video**
[LIST]
[*]Dimensions: 1920 x 1080
[*]Codec: N/A
[*]Framerate: 30 fps
[*]Bitrate: N/A
[/LIST]
**Audio**
[LIST]
[*]Codec: Dolby Digital (AC-3)
[*]Channels: Surround 5.1
[*]Sample rate: 48000 Hz
[*]Bitrate: 448 kbps
[/LIST][/INDENT]

Information given by SMPlayer:

[INDENT]**General**
[LIST]
[*]File
[*]Size: 25110720 KB (24522 MB)
[*]Length: 00:00:00
[*]Demuxer: mpegts
[/LIST]

**Video**
[LIST]
[*]Resolution: 1920 x 1088
[*]Aspect ratio: 1.7778
[*]Format: 0x10000005
[*]Bitrate: 0 kbps
[*]Frames per second: 29.970
[*]Selected codec: ffh264vdpau
[/LIST]

**Initial Audio Stream**
[LIST]
[*]Format: 8192
[*]Bitrate: 448 kbps
[*]Rate: 48000 Hz
[*]Channels: 2
[*]Selected codec: ffac3
[/LIST][/INDENT]

---

### Post by mrsah on 2012-01-28
Anyone any idea please?

---

