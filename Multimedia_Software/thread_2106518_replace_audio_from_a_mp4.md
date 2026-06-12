---
title: "replace audio from a mp4"
date: 2013-01-19
forum: Multimedia Software
---

### Post by greg_ory on 2013-01-19
Hi there,

I need some help to replace the audio stream from a mp4-file with my own mp3-file.

Here the output:

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '26.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 1
    compatible_brands: mp42avc1
    creation_time   : 2013-01-18 11:35:28
    comment         : SANYO DIGITAL CAMERA CG20
    comment-eng     : SANYO DIGITAL CAMERA CG20
  Duration: 00:01:06.13, start: 0.000000, bitrate: 17809 kb/s
    Stream #0.0(eng): Video: h264 (Main), yuvj420p, 1920x1080 [PAR 1:1 DAR 16:9], 17409 kb/s, 59.94 fps, 59.94 tbr, 60k tbn, 59.94 tbc
    Metadata:
      creation_time   : 2013-01-18 11:35:28
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 254 kb/s
    Metadata:
      creation_time   : 2013-01-18 11:35:28
At least one output file must be specified


Thanks in advance

-Greg

---

### Post by ron999 on 2013-01-19
> **greg_ory said:**
> 
I need some help to replace the audio stream from a mp4-file with my own mp3-file.


Hi

MP4Box will do it.
Use this command to isolate the video track:-
```
MP4Box 26.mp4 -single 1 -out video
```

Then add the soundtrack:-
```
MP4Box video.mp4 -add soundtrack.mp3
```

---

### Post by greg_ory on 2013-01-19
> **ron999 said:**
> Hi

MP4Box will do it.
Use this command to isolate the video track:-
```
MP4Box 26.mp4 -single 1 -out video
```

Then add the soundtrack:-
```
MP4Box video.mp4 -add soundtrack.mp3
```

That worked partly:

here the length of the two files:

2:49 min audio

1:07 min video

The Video freeze know at 1:07 min and the audio go's on until 2:49 min...just wondering how to bring both together nicely.

Thanks

-Greg

---

### Post by greg_ory on 2013-01-19
> **greg_ory said:**
> That worked partly:

here the length of the two files:

2:49 min audio

1:07 min video

The Video freeze know at 1:07 min and the audio go's on until 2:49 min...just wondering how to bring both together nicely.

Thanks

-Greg


Ok, found a way:

Command 1: MP4Box input_file.mp4 -single 1 -out video

Command 2: ffmpeg -i input_file.mp4 -i audio.mp3 -vcodec copy -shortest output.mp4

Source for the second command:
[http://stackoverflow.com/questions/13041061/mix-audio-video-of-different-lengths-with-ffmpeg](http://stackoverflow.com/questions/13041061/mix-audio-video-of-different-lengths-with-ffmpeg)

Thanks

-Greg

---

### Post by evilsoup on 2013-01-19
You can do that with a single ffmpeg command:

```

ffmpeg -i input.mp4 -i input.mp3 -map 0:v -map 1:a -c:v copy -shortest output.mp4

```

This will encode the audio to AAC; you may want to read [this AAC encoding guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide) for information on controlling the quality of the audio.

`-map 0:v -map 1:a` tells ffmpeg to take the video from input 0 (the first input, 'input.mp4'), and take the audio from input 1 (the second input, 'input.mp3').

---

### Post by greg_ory on 2013-01-19
> **evilsoup said:**
> You can do that with a single ffmpeg command:

```

ffmpeg -i input.mp4 -i input.mp3 -map 0:v -map 1:a -c:v copy -shortest output.mp4

```

This will encode the audio to AAC; you may want to read [this AAC encoding guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide) for information on controlling the quality of the audio.

`-map 0:v -map 1:a` tells ffmpeg to take the video from input 0 (the first input, 'input.mp4'), and take the audio from input 1 (the second input, 'input.mp3').

I guess I need a newer version of ffmpeg

Unrecognized option 'c:v'
Failed to set value 'copy' for option 'c:v'

---

### Post by evilsoup on 2013-01-19
For older versions, use -vcodec instead of -c:v.

-map 0:v -map 1:a also might not work, you may have to use `-map 0:0 -map 1:0` (which takes the first stream from each input (video is normally the first stream for videos, for audio obviously the audio will be the first stream); I don't know how recent the addition of 0:v and 0:a are).

There's a PPA for getting a more recent version of ffmpeg [here](https://launchpad.net/~jon-severinsson/+archive/ffmpeg). I would seriously recommend doing so, and not just because of the (superior IMO) modern syntax - you will gain access to a *lot* of bugfixes and improvements that have been made over time.

---

