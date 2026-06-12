---
title: "Remove video and keep audio"
date: 2010-09-03
forum: Multimedia Software
---

### Post by FinalShot on 2010-09-03
I'm trying to remove the video from a clip, and keep the audio, currently I'm trying this in OpenShot. But I don't think it's possible.

What programs can do this? If open shot can, how? I tried just rendering out the audio, but I can't not render the video it appears.

---

### Post by andrew.46 on 2010-09-04
Hi FinalShot,

FFmpeg can do this quite easily. Just beef up your copy of FFmpeg a little:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then could you post the full command and terminal output of the following command:

```
ffmpeg -i *my_file*
```

substituting 'my_file' for the actual name of* your *file. The syntax to strip out either video or audio can then be pointed out to you :).

All the best,

Andrew

---

### Post by FinalShot on 2010-09-04
```
scott@scott-desktop:~/Music$ ffmpeg -i lpp.MP4
Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'lpp.MP4':
  Duration: 00:03:12.76, start: 0.000000, bitrate: 667 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x264, 25 tbr, 25 tbn, 50 tbc
At least one output file must be specified
```

Don't know why it says one input file needs to be specified, as I did.

---

### Post by cotcot on 2010-09-04
It is easy with Avidemux.
Open the video in avidemux. Select "encoder" from the audio tab and choose the file format you want in the drop down menu you get when you click the copy button. Click OK. Then click "save", give a filename with the extension of the encoder you have choose ( mysound.mp3 for example) and OK.

---

### Post by andrew.46 on 2010-09-04
Hi Finalshot,

A nice easy one :). To get sound alone, which will be aac sound btw:

```
ffmpeg -i lpp.MP4 -vn -acodec copy lpp_audio_only.mp4
```

You can alter the filename as you please, technically you could also name the file *lpp_audio_only.**[COLOR="Red"]m4a[/COLOR]*** but this does not really matter.

All the best,

Andrew

---

