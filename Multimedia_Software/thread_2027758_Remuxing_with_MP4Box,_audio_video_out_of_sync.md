---
title: "Remuxing with MP4Box, audio video out of sync"
date: 2012-07-16
forum: Multimedia Software
---

### Post by danman33 on 2012-07-16
I have an .mkv video file containing H264 video and AC-3 audio, which I wanted to remux for playback on a playstation 3. I extracted the tracks using mkvextract, converted the audio to AAC using FFmpeg, and remuxed it to .MP4 using MP4Box. Now the audio and video are out of sync, and it gets worse as it goes on, so remuxing it with MP4Box with an audio delay won't fix it. What should I do to get this to an .MP4 file with H264 and AAC without reencoding the video? Thanks for any advice.

---

### Post by papibe on 2012-07-17
Hi danman33.

Having done the exactly same procedure myself a few times, I reckon there are two steps in which your audio can go out of sync.

First one is the the ffmpeg conversion: you have to keep the same audio bit rate as the original audio track. That means using the parameter **-ab** explicitly on the command.

Second is in the creation of the mp4 container itself: you have to match the frames per second as the original mkv. Use the option **-fps** for that.

Just a few thoughts. I hope they help.
Regards.

---

### Post by danman33 on 2012-07-17
I tried using the **-ab** parameter of ffmpeg and set it to the same bitrate as the original .ac3 audio stream and then remuxed it with MP4Box using **:fps=23.976** which I got using mkvinfo. The audio is still out of sync...

---

### Post by beandog on 2012-07-17
Try using ffmpeg to remux it, and encode the audio at the same time:

ffmpeg -i input.mkv -c:v copy -ab 256k output.mp4

---

### Post by danman33 on 2012-07-17
okay, but should i leave the audio bitrate the same as the origional? 448k?

---

### Post by beandog on 2012-07-17
> **danman33 said:**
> okay, but should i leave the audio bitrate the same as the origional? 448k?

No, that is really high.  I wouldn't go over 256k

---

### Post by danman33 on 2012-07-17
okay ```
ffmpeg -i input.mkv -c:v copy -ab 256k output.mp4
``` didnt even work. I tried ```
ffmpeg -i input.mkv -vcodec cpoy -acodec libfaac -ab 256k output.mp4
``` and I get this output. 
[B][mp4 @ 0x86dd940] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -83 >= -83
av_interleaved_write_frame(): Invalid argument[/B]
Any ideas as to what I'm doing wrong?

---

### Post by ron999 on 2012-07-17
> **danman33 said:**
> 
Any ideas as to what I'm doing wrong?
Show the full uncut terminal output.

---

### Post by danman33 on 2012-07-17
This is the output:

[B]dan@Laptop ~/Videos/2 $ ffmpeg -i R.mkv -vcodec copy -acodec libfaac -ab 448000 output.mp4
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x8bdd260] max_analyze_duration reached
[matroska,webm @ 0x8bdd260] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 23.98 (24000/1001)
Input #0, matroska,webm, from 'R.mkv':
  Metadata:
    title           : Reservoir.Dogs.1992.720p.BRRip.x264-x0r
  Duration: 01:39:07.94, start: 0.000000, bitrate: 448 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x544 [PAR 1:1 DAR 40:17], 23.98 fps, 23.98 tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s (default)
    Stream #0.2(eng): Subtitle: [0][0][0][0] / 0x0000 (default)
File 'output.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'output.mp4':
  Metadata:
    title           : Reservoir.Dogs.1992.720p.BRRip.x264-x0r
    encoder         : Lavf53.21.0
    Stream #0.0(eng): Video: libx264, yuv420p, 1280x544 [PAR 1:1 DAR 40:17], q=2-31, 1k tbn, 1k tbc (default)
    Stream #0.1(eng): Audio: libfaac, 48000 Hz, 5.1, s16, 448 kb/s (default)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
[mp4 @ 0x8be3940] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -83 >= -83
av_interleaved_write_frame(): Invalid argument[/B]

---

### Post by ron999 on 2012-07-17
Hi
This error:-
```
Application provided invalid, non monotonically increasing dts to muxer in stream
```
is probably because of this FFmpeg version:-
```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1
```

---

### Post by danman33 on 2012-07-17
should I update or compile my own?

---

### Post by flemur13013 on 2012-07-17
If all else fails, "avidemux" can either (assuming the formats are OK):
 - take your audio and video (separate) files and make your output file. 
 - take your original file and convert it.
In either case it has an **audio time shift** that you can preview and fiddle with until it's right (use the value under "filters", the main GUI setting doesn't always take).

---

### Post by ron999 on 2012-07-17
> **danman33 said:**
> should I update or compile my own?
Hi
Try this one first ---> [http://ffmpeg.gusari.org/static/](http://ffmpeg.gusari.org/static/)


With this command:-

```
./ffmpeg -i R.mkv -vcodec copy -acodec libvo_aacenc -ab 192k -ar 48000 -ac 2 output.mp4
```

---

### Post by danman33 on 2012-07-17
I compiled the latest ffmpeg and it gives me the same output, i also tried the static release, same problem. I think I'll give avidemux a shot.

---

### Post by beandog on 2012-07-17
> **danman33 said:**
> okay ```
ffmpeg -i input.mkv -c:v copy -ab 256k output.mp4
``` didnt even work. I tried ```
ffmpeg -i input.mkv -vcodec cpoy -acodec libfaac -ab 256k output.mp4
``` and I get this output. 
[B][mp4 @ 0x86dd940] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -83 >= -83
av_interleaved_write_frame(): Invalid argument[/B]
Any ideas as to what I'm doing wrong?

Typo?  Should be 'copy'

Also, you don't need to set acodec, it'll default to AAC, and in fact it might be using the wrong AAC encoder (there are a few, iirc).

---

