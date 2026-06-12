---
title: "Video conversion ... without the video."
date: 2011-06-27
forum: Multimedia Software
---

### Post by Shibblet on 2011-06-27
I am in the process of turning my DVD collection into MKV files, with Handbrake, for use on my HTPC.

Now, I am making MKV's with x264 as the video codec, and keeping the AC3 or DTS original audio.  I am not converting the sound for better playback on my receiver.

What I would like to know, is since the video is already done in x264, but the audio hasn't been converted, is there any way to just convert the audio to AAC without the time consuming portion of re-encoding the video?

Ideally, I'd like to drop in my MKV and output an MP4 with AAC 2-Channel Audio for playback on a separate device.  I know I can do this with Handbrake, but Handbrake will re-encode the video too, turning this into a lengthy process.  I'm looking for a quick conversion process.

Any help would be greatly appreciated.  Thanks.

---

### Post by andrew.46 on 2011-06-28
> **Shibblet said:**
> What I would like to know, is since the video is already done in x264, but the audio hasn't been converted, is there any way to just convert the audio to AAC without the time consuming portion of re-encoding the video?

I am not familiar with handbrake but it can certainly be accomplished with FFmpeg by specifying the audio changes and simply using *-vcodec copy* for the video stream.

---

### Post by Shibblet on 2011-07-03
Found it.  Its called Avidemux.  It will re/transcode your audio, video, and subtitles into any container format.  This is the ultimate conversion tool.

---

### Post by Shibblet on 2011-07-07
Avidemux doesn't work the way I need it to.  It causes audio/video desync.  In other words the audio doesn't line up with the video.

---

### Post by noshelter on 2011-07-08
why not only encode new audio and put it in an .mkv with the video?

> ffmpeg -i input.mkv -acodec ac3 -aq 48000 -ab 640k output.ac3You can change the codec/bitrate to your preference.

Then use MKV Creator or something. I'm not sure how to output .mp4 though

---

### Post by FakeOutdoorsman on 2011-07-12
> **Shibblet said:**
> Ideally, I'd like to drop in my MKV and output an MP4 with AAC 2-Channel Audio for playback on a separate device.

Another Alaskan? Not too many here. As andrew.46 mentioned FFmpeg should be able to do this:
```
ffmpeg -i input.mkv -vcodec copy -acodec libfaac -aq 100 -ac 2 output.mp4
```
You may need to add libfaac support to the repository FFmpeg first:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you get the "Can not resample 6 channels" error, then you'll need to compile FFmpeg (or process the audio with SoX). There's an easy guide that shows how to compile FFmpeg on Ubuntu:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I recommend using a compiled FFmpeg as >2 channel audio is not rare.

---

