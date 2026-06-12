---
title: "[SOLVED] tcdemux media stream determination"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by jabster on 2007-12-21
Hi.

Could someone please answer me a hopefully quick question about tcdemux and videa & audio streams?

I have used mplayer to rip my DVDs to a VOB file, and am using tcdemux to get rid of the audio streams I don't want.

From the man page:```
-A n[,m[,...]]
    Select packets using an identifier for extracting only selected streams without processing. This is useful for size reduction of your multimedia stream. Example: 

tcdemux -i big_dvd.vob -A 0xe0,0x81,0x20 > small_dvd.vob

extracts all packets for the video stream, AC3 audio track (1) and the first subtitle stream (0).
```

Where do the 0xe0, 0x81 & 0x20 come from? And what if I want the third audio track (stream 130 or whatever on the DVD)?

thanks,
john

---

### Post by disturbed1 on 2008-01-18
A vob file is multiplexed with stream identifiers. Upto 2 Video streams, 32 audio, and 32 subtitle tracks. Each stream has it's own, 

0xe0 = video
0x81 = audio
0x20 = subtitle

You can use tcprobe -i file.vob to get the information from it.

Or just rip with mplayer using the aid switch. (-aid 128 ) or -alang (2 letter country code)
 mplayer dvd://1 -v
This will give you the aids

DVD successfully opened.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (5.1) language: fr aid: 130.

or 
lsdvd -a
~$ lsdvd -a
Disc Title: ITALIAN_JOB
Title: 01, Length: 01:50:25.266 Chapters: 16, Cells: 33, Audio streams: 03, Subpictures: 02
        Audio: 1, Language: en - English, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 6, AP: 0, Content: Undefined, Stream id: 0x80
        Audio: 2, Language: en - English, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 2, AP: 0, Content: Undefined, Stream id: 0x81
        Audio: 3, Language: fr - Francais, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 6, AP: 0, Content: Undefined, Stream id: 0x82

---

### Post by jabster on 2008-01-18
Thanks disturbed1.

lsdvd is nice to know.

However, I also found out that 0x81 is hexdecimal. It's been a LONG time since I've dealt with those, so I didn't recognize that right away. I actually thought I had replied to myself saying that I figured it out, but either I'm wrong, or it was in a different thread of mine.

thanks for the info.

-john

---

