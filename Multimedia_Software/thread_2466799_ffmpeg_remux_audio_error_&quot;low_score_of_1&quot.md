---
title: "ffmpeg remux audio error &quot;low score of 1&quot;"
date: 2021-09-06
forum: Multimedia Software
---

### Post by steve234 on 2021-09-06
Hi there,

I have a video editor which is picky about framerate on one of my PCs. I typically use two types of footage from two cameras both of which need to be converted to "edit friendly" 30fps fixed timecode.

I can change the framerate of both in the usual way with ffmpeg:

```
ffmpeg -i <input> -filter:v fps=fps=30 <output>
```

But this is:

(1) slow; and
(2) causes a re-encode of one type of file to a terribly blocky output (the output for the other type is acceptable). 

I'm therfore now trying to change the framerate, without re-encoding, as per answer 4 of [ this stackexchange question ](https://stackoverflow.com/questions/45462731/using-ffmpeg-to-change-framerate/45465730).

This works *perfectly* for one filetype, but not the other.

The files I'm having difficulty with have the following properties:

```
Metadata:
      creation_time   : 2012-03-12T23:11:14.000000Z
      handler_name    : VideoHandler
      encoder         : h264
    Stream #0:1(eng): Audio: pcm_s16le (sowt / 0x74776F73), 32000 Hz, mono, s16, 512 kb/s (default)
    Metadata:
```
    
On the audio step of the tutorial the error is:

```
Only AAC streams can be muxed by the ADTS muxer
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument
```

I have a similar result if try the full remux. 

```
ffmpeg -probesize "42M" -y -r 30 -i output_raw_bitstream.h264 -i output-audio.aac -c copy REC_0001_output_1.mp4
```

I've hit a dead-end with researching pcm_s16le / AAC incompatibility in ffmpeg. I saw someone had written a "fix" in C, but didn't understand it, or how to leverage it to help my workflow. 

Any help would be appreciated.

---

### Post by steve234 on 2021-09-06
Solved:

do this method:

```

# Extract video stream
ffmpeg -y -i input_video.mp4 -c copy -f h264 output_raw_bitstream.h264
# Extract audio stream
ffmpeg -y -i input_video.mp4 -vn -acodec copy output_audio.aac
# Remux with new FPS 
ffmpeg -y -r 24 -i output_raw_bitstream.h264 -i output-audio.aac -c copy output.mp4
```

but use ```
 -acodec aac 
``` in place of ```
 -acodec copy 
``` for pcm_s16le audio. That changes it to aac which the remuxer can work with

---

