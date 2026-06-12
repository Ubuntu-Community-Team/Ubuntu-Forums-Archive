---
title: "ffmpeg &amp; dvb help needed?"
date: 2012-12-23
forum: Multimedia Software
---

### Post by Merrattic on 2012-12-23
Looking for new ways to capture and transcode dvb-t and decided to give ffmpeg/ffplay a try. Documentation on this is sparse to say the least.

To date, I have used mplayer to capture the stream, running a short script with zenity in order to select the channel and length of time to record. The mplayer part is simplicity itself, scan creates the mplayer compliant channels.conf (I'll use BBC1 as the channel):
```
mplayer dvb://BBC1 -dumpstream -dumpfile output.ts
```In order to get good a/v sync, the only method I have found is to demux the video and audio using ProjectX, then to encode each part and then remux with mencoder. This has served me well for years. (I have a cache of 8192 in the config file)

Looking at what ffmpeg has to offer, things are a bit trickier.

First one has to lock onto a channel using tzap:
```
tzap -r -c ~/.mplayer/channels.conf "BBC1"
```then leave this running in a terminal, then in a new terminal:```
 ffplay -i /dev/dvb/adapter0/dvr0
``` This opens a playing window for @ 3 seconds and then freezes. This all seems a bit messy. I haven't found a way to get ffmpeg/ffplay to lock onto a channel by itself, although there is some stuff in the documentation about -f mpegts but I can't find anything more on this.

I am aware one can tzap a channel then directly output that to a file, or to use cat to do this.

My eventual aim would be to lock onto the channel, then serve it up to my local lan so the same channel can be streamed/viewed on all PCs all over the LAN.

Has anyone else had any luck in this area? I am also interested in how to use ffmpeg to allow "my" .ts streams (generated with mplayer) to be searchable without necessarily re-encoding, or how to directly re-encode whilst maintaining good a/vsync.

If it helps, here is some output from ffmpeg on a .ts stream captured using tzap:
```
ffmpeg -i test.ts
ffmpeg version git-2012-09-12-ddc9bc7 Copyright (c) 2000-2012 the FFmpeg developers
  built on Sep 12 2012 21:05:07 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      51. 72.100 / 51. 72.100
  libavcodec     54. 55.100 / 54. 55.100
  libavformat    54. 26.101 / 54. 26.101
  libavdevice    54.  2.100 / 54.  2.100
  libavfilter     3. 16.103 /  3. 16.103
  libswscale      2.  1.101 /  2.  1.101
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[mpeg2video @ 0x962bc00] mpeg_decode_postinit() failure
    Last message repeated 2 times
[mpegts @ 0x9613540] max_analyze_duration 5000000 reached at 5000000
[mpegts @ 0x9613540] Could not find codec parameters for stream 2 (Audio: mp3 ([3][0][0][0] / 0x0003), 0 channels, s16): unspecified frame size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 4 (Unknown: none ([5][0][0][0] / 0x0005)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 5 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 6 (Unknown: none ([13][0][0][0] / 0x000D)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 7 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 8 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 9 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 10 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 11 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0x9613540] Could not find codec parameters for stream 12 (Unknown: none ([11][0][0][0] / 0x000B)): unknown codec
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[NULL @ 0x962ff00] start time is not set in estimate_timings_from_pts
[NULL @ 0x9631760] start time is not set in estimate_timings_from_pts
[NULL @ 0x9633100] start time is not set in estimate_timings_from_pts
[NULL @ 0x96336a0] start time is not set in estimate_timings_from_pts
[NULL @ 0x9634f60] start time is not set in estimate_timings_from_pts
[NULL @ 0x96368c0] start time is not set in estimate_timings_from_pts
[NULL @ 0x9638360] start time is not set in estimate_timings_from_pts
[NULL @ 0x9638920] start time is not set in estimate_timings_from_pts
[NULL @ 0x963a300] start time is not set in estimate_timings_from_pts
[NULL @ 0x963a8c0] start time is not set in estimate_timings_from_pts
[NULL @ 0x963c180] start time is not set in estimate_timings_from_pts
[mpegts @ 0x9613540] PES packet size mismatch
Input #0, mpegts, from 'test.ts':
  Duration: 00:25:47.65, start: 91915.364067, bitrate: 2904 kb/s
  Program 4163 
  Program 4287 
    Stream #0:0[0xc9]: Video: mpeg2video (Main) ([2][0][0][0] / 0x0002), yuv420p, 720x576 [SAR 64:45 DAR 16:9], 15000 kb/s, 25.17 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0:1[0xca](eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, stereo, s16, 256 kb/s
    Stream #0:2[0xce](eng): Audio: mp3 ([3][0][0][0] / 0x0003), 0 channels, s16 (visual impaired)
    Stream #0:3[0xcd](eng): Subtitle: dvb_subtitle ([6][0][0][0] / 0x0006)
    Stream #0:4[0xfa]: Unknown: none ([5][0][0][0] / 0x0005)
    Stream #0:5[0xd2]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:6[0xd7]: Unknown: none ([13][0][0][0] / 0x000D)
    Stream #0:7[0x1ce9]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:8[0x1c21]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:9[0x1c22]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:10[0x1c23]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:11[0x1c24]: Unknown: none ([11][0][0][0] / 0x000B)
    Stream #0:12[0x1c25]: Unknown: none ([11][0][0][0] / 0x000B)
  Program 4288 
  Program 4352 
  Program 4416 
  Program 4544 
  Program 4608 
  Program 4672 
  Program 4736 
  Program 5632 
  Program 5696 
  Program 5760 
  Program 5824 
  Program 5888 
  Program 5952 
  Program 6016 
  Program 6720 
  Program 6784 
  Program 6848 
  Program 6912 
  Program 7168 
  Program 7232 
At least one output file must be specified
```

---

