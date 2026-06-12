---
title: "Gstreamer failing to play some mp3s playable by mpg123 and mplayer."
date: 2013-12-16
forum: Multimedia Software
---

### Post by neltnerb on 2013-12-16
I have a strange new problem (I think) in Ubuntu 13.10. For several mp3s I have been using for many years, they no longer play in clementine (using gstreamer). However, they play perfectly fine in mplayer.

Converting them back to wav with mpg123 and then re-encoding them fixes the problem, but they are correct enough for mplayer and mpg123 to decode, and gstreamer decoded them fine in the past (I think).

It's particularly odd in that it affects perhaps one song on an entire CD I ripped back in 2010. The others which were encoded at the same time with the same settings have no problem. This has happened on at least two albums, Miles Davis "Kind of Blue" and Shpongle "Nothing Lasts...". I'd like to either fix gstreamer to be able to properly decode these seemingly fine files, or else find a program that will go through my entire music collection and fix whatever header inconsistency or other strangeness is causing a problem.

gst-typefind for both 1.0 and 0.10 versions both output:
```
08 - ...But Nothing Is Lost.mp3 - application/x-id3
```
for the broken file and
```
07 - Shnitzled in the Negev.mp3 - application/x-id3
```
for a working file made at the same time from the same source with the same settings.

The actual error gstreamer throws is "GStreamer encountered a general stream error."

mp3check -e outputs nothing notable except:
```
08 - ...But Nothing Is Lost.mp3
4593 bytes of junk before first frame header
valid id3 tag trailer v1.1 found
frame     1/ 0:00: bitrate switching (256 -> 320)
frame     2/ 0:00: bitrate switching (320 -> 256)
...
frame 10667/ 4:38: bitrate switching (192 -> 224)
frame 10668/ 4:38: sync error (frame too long) at 0x00868df2, skipping 303 bytes at 0x008690cd
frame 10670/ 4:38: bitrate switching (224 -> 256)
frame 10671/ 4:38: bitrate switching (256 -> 32)
```

while for the working file it gives:
```
07 - Shnitzled in the Negev.mp3:
4906 bytes of junk before first frame header
valid id3 tag trailer v1.1 found
frame     1/ 0:00: bitrate switching (256 -> 320)
frame     2/ 0:00: bitrate switching (320 -> 224)
...
frame  9846/ 4:16: bitrate switching (224 -> 320)
frame  9854/ 4:17: sync error (frame too short) at 0x007d6d3a, 10 bytes mising
frame  9857/ 4:17: bitrate switching (320 -> 256)
frame  9858/ 4:17: bitrate switching (256 -> 192)
```

I tried renaming the "broken" file to eliminate the ellipses, but that did not change anything. And considering that I have Sigur Rós songs like "Ágætis byrjun", I don't think it's likely to be a character encoding issue (although those files are flac, not mp3).

So the mystery is that by all inspection tools I know how to use, these two mp3s have essentially identical profiles. Same version of id3 tag, some junk before the first frame for some reason, bitrate switching throughout, a sync error due to a too short frame two frames before the end for some reason, but consistent between them. Yet one plays fine with gstreamer in clementine while the other throws an error.

Unfortunately, with copyright oppression I can't upload the actual files even for this unrelated purpose, but if there are any ideas for either repairing the mp3s or testing them further, please let me know.

The problem is not limited to clementine, I also could not use sound converter to handle re-encoding the file (same gstreamer error). However, I was able to re-encode with mpg123 and lame. But that is both annoying, lossy, and requires me to redo all the ID3 tags.

---

