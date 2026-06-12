---
title: "Problems w/ video coding"
date: 2014-04-11
forum: Multimedia Software
---

### Post by colmeweb on 2014-04-11
So I have been trying to merge a new sound clip into a video using openshot and the file I output is either a massive size, crappy quality, or both. The original movie is 1 hour long and 462.5 Mb, the sound clip I am trying to edit in is 2.5 Mb, and the copy I made of the original sound for the video is 89.8 Mb. I keep using mp4 h264 settings. I tried decreasing the video bit rate from 5 Mb/s to 1.25 Mb/s. but the picture quality dropped.

Are there any settings in openshot that will maintain the original quality without putting the file size above 2 Gb?

I tried installing cinelerra, but it doesn't show in any directory. So if anybody has any advice on that one that would be great.

The basic info for the original video is attached below.

[ATTACH=CONFIG]251944[/ATTACH][ATTACH=CONFIG]251945[/ATTACH]

Thanks for any help

---

### Post by FakeOutdoorsman on 2014-04-13
Assuming both audio inputs are stereo, by "merge" do you mean you want to:

[list=1]
[*]combine the original audio and new audio into one two-channel (stereo) audio stream, or
[*]combine the original audio and new audio into one four-channel audio stream, or
[*]add the new audio as a separate stream, so the output contains one video stream and two separate audio streams, or
[*]replace the original audio with the new audio
[/list]

---

### Post by colmeweb on 2014-04-14
I am trying to insert a small bit of new audio on one part of the video.
What I did was. (See picture for quick reference)

1. Make an aac copy of the original video's audio track.
2. Load both the original video and the copied audio track into openshot. (Tracks 1 and 2)
3. Load the short audio clip into openshot. (Track 3)
4. Mute the audio portion of the original video.
5. Clip out the portion I wish to change.

The video works well, but the image is grainy. 
I'm just looking for the right settings to get an image quality & file size similar to the original.

[ATTACH=CONFIG]252041[/ATTACH]

---

### Post by FakeOutdoorsman on 2014-04-14
If you don't mind a command-line tool you can use ffmpeg to manipulate the audio while leaving the video untouched (unless of course you want to re-encode it to a different format).

1. Get ffmpeg. The version in the repository is a fake and does not have the features required. Also, it's recommended to occasionally update to a new build since development is very active. You can simply download a [Linux build of ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

2. Use the atrim and concat filters to choose the sections of audio and then concatenate them. This example will use 0-4 seconds of audio from video.mp4, the audio from duration 12-15 (3 seconds) from audio.m4a, and then 7-end from video.mp4 (notice the **./** before the ffmpeg in case you downloaded a build so you don't use the crappy, fake version from the repo).

```

./ffmpeg -i video.mp4 -i audio.m4a -filter_complex \
"[0:a]atrim=end=4,asetpts=PTS-STARTPTS[a0]; \
 [1:a]atrim=12:15,asetpts=PTS-STARTPTS[a1]; \
 [0:a]atrim=start=7,asetpts=PTS-STARTPTS[a2]; \
 [a0][a1][a2]concat=n=3:v=0:a=1[audio]" \
-map 0:v -map "[audio]" -codec:v copy -shortest output.mp4
```

This will [stream copy](https://ffmpeg.org/ffmpeg.html#Stream-copy) the video so no re-encoding of the video will occur. See the [FFmpeg Filters Documentation](https://ffmpeg.org/ffmpeg-filters.html) for more info in each filter.

---

