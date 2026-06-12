---
title: "MKV, DTS to AC3 with FFMPEG. Output can't seek forward or backward.."
date: 2011-11-15
forum: Multimedia Software
---

### Post by oblador on 2011-11-15
Hi,

I'm working on a MKV video file.

I converted its DTS sound stream to AC3 using ffmpeg.

It's possible to seek backwards or forwards using VLC, SMplayer, or any other video player software.

But when I try to play it on my BluRay (Samsung bd p1600), it's impossible to seek backwards or forwards, I can only play it continuosly.

What can I do in order to convert the DTS sound track to AC3 and keep the possibility of seeking backwards and forwards?


Thanks.

PS: this is how I converted the DTS sound stream to AC3:


1-this is how I extracted the audio track and converted it to AC3:
ffmpeg -i input.mkv -acodec ac3 -ab 640k output.ac3

2-this is how I joined the video file with the sound file:

ffmpeg -i input.mkv -i output.ac3 -vcodec copy -acodec copy -sn output.mkv -map 0.0 -map 1.0

---

### Post by FakeOutdoorsman on 2011-11-16
Those two commands could probably be combined:
```
ffmpeg -i input.mkv -vcodec copy -acodec ac3 -ab 640k output.mkv
```
Is the Samsung player able to seek other MKV files, or is this video particularly troublesome? Do you have the latest firmware for the player? Some network connected models have an easy method to update.

Maybe the Samsung doesn't like how FFmpeg muxed the MKV, and the [mkclean](http://ubuntuforums.org/showpost.php?p=10737124&postcount=1653) tool could be useful in this instance. Note that the latest version is 0.8.6.

To summarize: I don't really know.

---

