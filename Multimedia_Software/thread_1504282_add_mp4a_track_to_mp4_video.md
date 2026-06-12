---
title: "add mp4a track to mp4 video"
date: 2010-06-07
forum: Multimedia Software
---

### Post by jimmy the saint on 2010-06-07
So I have an mp4 video which includes a 5.1 audio stream, while I only have stereo speakers from my computer.  It is hooked up to my receiver through the audio out (headphone) jack from the back of the machine.  Anyway, I have a stereo audio stream for the video, but I can't figure out how to add the mp4a stream to the mp4.  

I have checked out avidemux, but it doesn't seem to handle mp4a files.  I don't want to transcribe the video, simply add the audio to the mp4 container.  Does anyone know haw to accomplish this in Ubuntu?  Thanks

PS It seems that the mp4a is us encoded as AAC

---

### Post by ron999 on 2010-06-07
Hi
Maybe there's an easier way, but here's a first attempt.

1 Extract the raw video track from the video file using ffmpeg.
```
ffmpeg -i movie.mp4 -an -vcodec copy video.m4v
```

2 Extract the raw audio track from the video file using ffmpeg.
```
ffmpeg -i movie.mp4 -vn -acodec copy audio1.aac

```
3 Extract the raw audio track from your extra audio file using ffmpeg.
```
ffmpeg -i whatever.mp4a -vn -acodec copy audio2.aac

```
4 Use MP4Box to mux the 3 tracks.
```
MP4Box -add video.m4v -add audio1.aac -add audio2.aac newmovie.mp4

```

MP4Box is part of package **gpac**.

Are you certain that your extra audio file has extension **mp4a**?
That's unusual.

EDIT
It would be much less hassle if you use mkvmergeGUI. Part of the package **mkvtoolnix**.
This will create an mkv file containing the three tracks.

---

### Post by FakeOutdoorsman on 2010-06-08
ron999 is on the right track.  You could also use the *-map* option to do this in one command, although sometimes it can be tricky.  Example:
```
$ ffmpeg -i IronMan.mkv -i avatarhd.mp4
```
Pukes out a bunch of info, including:
```
Input #0, matroska, from '**IronMan.mkv**':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #[color=#FF6600]0.0[/color]: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 23.98 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16

Input #1, mov,mp4,m4a,3gp,3g2,mj2, from '**avatarhd.mp4**':
  Duration: 00:03:31.08, start: 0.000000, bitrate: 2106 kb/s
    Stream #[color=#FF6600]1.0[/color](und): Audio: aac, 44100 Hz, stereo, s16, 125 kb/s
    Stream #1.1(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 1978 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
```
I want video from IronMan.mkv (stream 0.0) and audio from avatarhd.mp4 (stream 1.0).  Combine:
```
ffmpeg -i IronMan.mkv -i avatarhd.mp4 -vcodec copy -acodec copy -map 0:0 -map 1:0 output.mkv
```
Well, I guess that's two commands...and I assumed you only wanted one audio stream.

---

