---
title: "muxing third audio stream (ffmpeg)"
date: 2011-07-31
forum: Multimedia Software
---

### Post by Blubbi_Blubbkekz on 2011-07-31
Hello,

I have one Video File (mpeg2) and three Audio Files (mpeg2)
and i want to mux them all together in one file
(to create a multilang DVD)
tried it using this ffmpeg command:

ffmpeg -i movie.m2v -i audio1.mp2 -i audio2.mp2 -i audio3-mp2 -acodec copy -vcodec copy newmovie.mpeg -newaudio

then i get this

Input #0, mpegvideo, from 'movie.m2v':
  Duration: 02:09:30.19, bitrate: 3799 kb/s
    Stream #0.0: Video: mpeg2video, yuv420p, 616x254 [PAR 508:693 DAR 16:9], 3800 kb/s, 25 fps, 25 tbr, 1200k tbn, 50 tbc
[mp3 @ 0x83d8da0]max_analyze_duration reached
[mp3 @ 0x83d8da0]Estimating duration from bitrate, this may be inaccurate
Input #1, mp3, from 'audio1.mp2':
  Duration: 02:17:10.41, start: 0.000000, bitrate: 192 kb/s
    Stream #1.0: Audio: mp2, 48000 Hz, 2 channels, s16, 192 kb/s
[mp3 @ 0x842da90]max_analyze_duration reached
[mp3 @ 0x842da90]Estimating duration from bitrate, this may be inaccurate
Input #2, mp3, from 'audio2.mp2':
  Duration: 02:17:11.49, start: 0.000000, bitrate: 192 kb/s
    Stream #2.0: Audio: mp2, 48000 Hz, 2 channels, s16, 192 kb/s
[mp3 @ 0x83f2c80]max_analyze_duration reached
[mp3 @ 0x83f2c80]Estimating duration from bitrate, this may be inaccurate
Input #3, mp3, from 'audio3.mp2':
  Duration: 03:55:23.64, start: 0.000000, bitrate: 192 kb/s
    Stream #3.0: Audio: mp2, 48000 Hz, 2 channels, s16, 192 kb/s
Output #0, mpeg, to 'newmovie.mpg':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: mpeg2video, yuv420p, 616x254 [PAR 173:236 DAR 13321:7493], q=2-31, 3800 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, 2 channels, 192 kb/s
    Stream #0.2: Audio: mp2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
  Stream #2.0 -> #0.2


and as you can see in the last 3 lines ffmpeg only takes 2 audio streams
i already tried muxing the first two audio streams to the video file and then add a third one (using the same command, just leave out the other two audio streams, and take the video already including the other two audio files), but this didnt work either, it just replaced one of the other audio streams...
is it possible to mux a third audio stream using ffmpeg or any other
program to a mpeg2 video file


thank you
Blubbi

---

