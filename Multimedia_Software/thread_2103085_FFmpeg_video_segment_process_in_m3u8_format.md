---
title: "FFmpeg video segment process in m3u8 format"
date: 2013-01-09
forum: Multimedia Software
---

### Post by Mediacentre on 2013-01-09
Dear team ,
I am new in ffmpeg , i would like to know how to convert mkv video in to m3u8 format & also segment the same?

please provide step by step process


Warm regards,
Sailm

---

### Post by evilsoup on 2013-01-09
M3U8 is a playlist file. I'm going to assume that you really want to split the file into multiple mpegts files, with an m3u8 playlist pointing to all the videos in order:

```

ffmpeg -i input.mkv -c copy -f segment -segment_list playlist.m3u8 -segment_time 10 output%03d.ts

```

-c copy means 'copy all the streams'; this means no transcoding, so it saves on CPU, time, and generational data loss. -f segment tells ffmpeg to output multiple segments, -segment_list playlist.m3u8 tells it to generate a playlist file called playlist.m3u8, -segment_time 10 means 'make a segment every ten seconds'. output%03d.ts means it will output mpegts files in the pattern of: output001.ts, output002.ts, output003.ts, and so on.

You can read more about the segment muxer [here](https://ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment). If you have any problems with this method, post back here with the full command and terminal output, contained within [code ][ /code] tags.

---

