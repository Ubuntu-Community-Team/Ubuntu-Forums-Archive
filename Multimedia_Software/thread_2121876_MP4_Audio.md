---
title: "MP4 Audio?"
date: 2013-03-03
forum: Multimedia Software
---

### Post by asearle on 2013-03-03
Hi Everyone,

I have been experimenting with OpenShot and with Kdenlive and they both seem to be powerful video editing tools.

However, I need to do a relatively simple thing and cannot seem to find the functionality for this in either of these tools:  What I need to do is to run an MP4 video and add a spoken commentary as the clip is running.  The video editing tools seem to offer the option of merging an audio track but I can't find an option which allows spoken audio to be added.

Can anyone help me with this?  Am I investigating the right tools?  If so, then where do I find the features/options I need.

Many thanks for any tips that you can give me.

Yours,
Alan

---

### Post by FakeOutdoorsman on 2013-03-03
If you already have the commentary and it is timed correctly for the video you can simply combine the video and audio. This has the advantage of copying the video so there is no re-encoding and no loss of video quality. This will add another audio stream, but not combine an existing audio stream in video.mp4 with audio.wav.
```
ffmpeg -i video.mp4 -i audio.wav -c:v copy -c:a libfaac -q:a 100 -shortest output.mp4
```
If you want to merge existing audio with the commentary into one audio stream:
```
ffmpeg -i video.mp4 -i audio.wav -filter_complex "amerge,pan=stereo:c0<c0+c2:c1<c1+c3" -c:a libfaac -q:a 100 -shortest output.mp4
```
See the documentation for more info on [amerge](http://ffmpeg.org/ffmpeg-filters.html#amerge) and [pan](http://ffmpeg.org/ffmpeg-filters.html#pan).

The input audio does not have to be WAV. This is just an example and you can use any format that ffmpeg can decode. 

Note that these examples are likely not to work with the libav fake "ffmpeg" from the repo. I'm using a recent compiled real ffmpeg. Get a [static build](http://ffmpeg.org/download.html#LinuxBuilds) if you don't feel like [compiling ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

I tested these commands using somewhat incongruent sources which made an interesting video...

---

### Post by asearle on 2013-03-04
Many thanks for these tips.

Yes, now I understand how it is intended to work and so can easily move forward.  That's excellent!

Yours,
Alan

---

### Post by asearle on 2013-03-08
As it was (following the hints in the tips given by Outdoorsman) I ...

a.) recorded the audio while the video was running (without sound) with the standard Linux Sound Recorder.
b.) I saved the audo file
c.) In OpenShot I imported both the video track and the audio track
d.) I switched off the sound on the video track
e.) I moved the audio track around so that that everything lined up with the video

Excellent.  Many thanks for the tip.

Yours,
Alan

---

### Post by asearle on 2013-03-08
As it was (following the hints in the tips given by Outdoorsman) I ...

a.) recorded the audio while the video was running (without sound) with the standard Linux Sound Recorder.
b.) I saved the audo file
c.) In OpenShot I imported both the video track and the audio track
d.) I switched off the sound on the video track
e.) I moved the audio track around so that that everything lined up with the video

Excellent.  Many thanks for the tip.

Yours,
Alan

---

