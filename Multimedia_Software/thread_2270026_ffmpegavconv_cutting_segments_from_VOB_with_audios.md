---
title: "ffmpeg/avconv cutting segments from VOB with audio/subtitle streams intact?"
date: 2015-03-19
forum: Multimedia Software
---

### Post by TheFu on 2015-03-19
Using Ubuntu server 14.04 (patched as of today) ... no GUI.

Been trying to cut up a large VOB file (mpegps) into 4 segments at specific locations.  This VOB file has 1 video stream, 1 audio stream, 3 subtitle streams and 1 closed caption. From the source, it is 1 title for all 4 segments, so I can't simply split it there.

This works as expected, but it starts at the beginning.
```
$ avconv -ss 0 -i total.vob -map 0  -c:v copy \
       -c:a copy -c:s copy -t 2649.2 105.vob

``` All the streams are copied and available in the output

The next segment or any without zero/0 for the start position fail.  A 52Kb file is created.
```
$ avconv -ss 2655.24 -i total.vob -map 0  -c:v copy \
       -c:a copy -c:s copy -t 2649.84 106.vob
```

ss = start position
t = duration (about 44 min in my cmds)

Tried using t as the end position - no joy.
Tried using ffmpeg - same issue.
Oh - and avconv is very picky about where the -t option goes for some reason ... or perhaps I has some other issue that was corrected.

Tried using avidemux on a different machine - it drops the extra streams, which isn't desired. I'm a language freak and want to keep them all, but cut into the desired segments.

Tried creating a big mkv/h.264/ac3/aac/sub/srt file and editing it - my cheap commercial editor drops the subs and extra languages.

Great - so added the recommended PPA from the ffmpeg website - now running ffmpeg v2.6 and tried again. No joy. 
```
ffmpeg -ss 2655.24 -i total.vob  -c:v copy -map 0 -c:a copy -c:s copy -t 2649.84  106.vob

ffmpeg version 2.6 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)

<snip> ... options/libs stuff

Input #0, mpeg, from 'total.vob':
  Duration: 00:00:12.01, start: 0.280633, bitrate: N/A
    Stream #0:0[0x1bf]: Data: dvd_nav_packet
    Stream #0:1[0x1e0]: Video: mpeg2video (Main), yuv420p(tv), 720x480 [SAR 8:9 DAR 4:3], max. 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0:2[0x80]: Audio: ac3, 48000 Hz, 5.1(side), fltp, 448 kb/s
    Stream #0:3[0x20]: Subtitle: dvd_subtitle
    Stream #0:4[0x21]: Subtitle: dvd_subtitle
    Stream #0:5[0x22]: Subtitle: dvd_subtitle
Data stream encoding not supported yet (only streamcopy)

```
Read that the last message was caused by using *-map 0*, so I removed that. No joy. Same 51Kb file created and no errors.

What is wrong?

---

### Post by mc4man on 2015-03-20
This thread *may* be relevant to your issue (as in maybe try -i  before -ss & -t
[http://ubuntuforums.org/showthread.php?t=1236223](http://ubuntuforums.org/showthread.php?t=1236223)

---

### Post by Keith_Helms on 2015-03-21
If you have it in an mkv file, wouldn't mkvmerge (package mkvtoolnix) work for you?  It does file splitting.

---

### Post by TheFu on 2015-03-22
Tried changing the order of the options for both ffmpeg and avconv - that didn't help. I would hope they used getopts() which should remove the need to have options specified in order ... besides the output-file-name which must come last. Oh well.

Didn't know that **mkvmerge** could split.  Tested it with a local file (cur on travel) and it retained all the streams in each part of the output. I can certainly do the split remotely, but can't easily validate the results for a few days. However, I did use the mkvmerge command and it did appear to work with the resulting correct splits AND all streams inside (according to mkvinfo). My confidence is extremely high with this answer.  Plus, the mkvmerge options are really easy to understand (since it doesn't need to added complexities from all the transcoding options of the other tools).

Just for an exact example for the next person:```

$ mkvmerge -o out.mkv \
   --split parts:-44:09.20,44:15.24-1:28:25.08,1:28:31.08-2:12:40.27,2:12:47.06-2:56:55.27 \
    total.mkv
```
I think it worked. Took a little over a minute, since it was really just copying the file and chunking into 4 parts. It should only split on key-frames. Hope those times are close enough. Sometime keyframes happen only every 10 seconds, other times they occur 3 times in a single second.

MKV rocks - once again.  I've been using MKV containers for almost 5 yrs now:
   [http://blog.jdpfu.com/2010/11/02/mkv-containers-why-use-them-scripts](http://blog.jdpfu.com/2010/11/02/mkv-containers-why-use-them-scripts)  - love some of the other things that can be fixed by modifying stream settings - like aspect ratios, correcting audio/video sync issues .. adding subs or srts.

While I don't use the GUI version of mkvmerge - there is one for people who might prefer that tool.

Thanks!  I'll mark this as solved after it is validated.

---

### Post by FakeOutdoorsman on 2015-03-22
Looks like you found a solution using mkvmerge, but when using ffmpeg does this command work?
```
ffmpeg -ss 2655.24 -i total.vob -map 0 -c copy -t 2649.84 106.vob
```
Using "-c copy" will tell ffmpeg to stream copy all stream types. That should avoid the "Data stream encoding not supported yet (only streamcopy)" message.

---

### Post by TheFu on 2015-03-22
> **FakeOutdoorsman said:**
> Looks like you found a solution using mkvmerge, but when using ffmpeg does this command work?
```
ffmpeg -ss 2655.24 -i total.vob -map 0 -c copy -t 2649.84 106.vob
```
Using "-c copy" will tell ffmpeg to stream copy all stream types. That should avoid the "Data stream encoding not supported yet (only streamcopy)" message.

Nope. Didn't work:

```

Input #0, mpeg, from 'total.vob':
  Duration: 00:00:12.01, start: 0.280633, bitrate: N/A
    Stream #0:0[0x1bf]: Data: dvd_nav_packet
    Stream #0:1[0x1e0]: Video: mpeg2video (Main), yuv420p(tv), 720x480 [SAR 8:9 DAR 4:3], max. 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0:2[0x80]: Audio: ac3, 48000 Hz, 5.1(side), fltp, 448 kb/s
    Stream #0:3[0x20]: Subtitle: dvd_subtitle
    Stream #0:4[0x21]: Subtitle: dvd_subtitle
    Stream #0:5[0x22]: Subtitle: dvd_subtitle
Output #0, svcd, to '106-foo.vob':
  Metadata:
    encoder         : Lavf56.25.101
    Stream #0:0: Data: dvd_nav_packet
    Stream #0:1: Video: mpeg2video, yuv420p, 720x480 [SAR 8:9 DAR 4:3], q=2-31, max. 9000 kb/s, 29.97 fps, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0:2: Audio: ac3, 48000 Hz, 5.1(side), 448 kb/s
    Stream #0:3: Subtitle: dvd_subtitle
    Stream #0:4: Subtitle: dvd_subtitle
    Stream #0:5: Subtitle: dvd_subtitle
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
  Stream #0:2 -> #0:2 (copy)
  Stream #0:3 -> #0:3 (copy)
  Stream #0:4 -> #0:4 (copy)
  Stream #0:5 -> #0:5 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted

```

Ok - back home now.
Tested the ffmpeg again - fails to work - same error as above, no output file(s) created.

Tested the mkvmerge results - vlc sees everything, but Kodi plays the 2 audio streams and captions, but none of the subs. It shows them in the list, but won't display. mkvinfo shows that the subs are there like VLC does.  Inside vlc the subs are black text and don't show up well. The sub color override isn't working.  The languages for the subs are undefined according to mkvinfo, however they were in the original as well.

Looks like mkvmerge is the best answer for me.

---

### Post by FakeOutdoorsman on 2015-03-23
I guess muxing of dvd_nav_packet is not yet supported. The error message isn't very informative unfortunately. The following should work:
```
ffmpeg -ss 2655.24 -i total.vob -map 0 -map -0:d -c copy -t 2649.84 106.vob
```

---

### Post by TheFu on 2015-03-24
> **FakeOutdoorsman said:**
> I guess muxing of dvd_nav_packet is not yet supported. The error message isn't very informative unfortunately. The following should work:
```
ffmpeg -ss 2655.24 -i total.vob -map 0 -map -0:d -c copy -t 2649.84 106.vob
```

Nope. Didn't work.
```
frame=    2 fps=0.0 q=-1.0 Lsize=      50kB time=00:00:00.67 bitrate= 609.5kbits/s    
video:7kB audio:38kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 9.835890%

```

I'm moving on the source for this test is gone now.  Thanks everyone!

---

### Post by FakeOutdoorsman on 2015-03-24
Odd. Worked for me with a seemingly similar input.

---

