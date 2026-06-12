---
title: "ffmpeg or avconv Not Editing"
date: 2014-02-13
forum: Multimedia Software
---

### Post by Geoff_Lane on 2014-02-13
I recorded a Uk TV program recently as a TS file, it shows as 1.2GB

Transferred it to my computer to edit it.

On one hardware media player it freezes after around 2 minutes, VLC the same and does not show time of video.

My Sony Bravia TV's built in media player plays it fine.

Neither ffmpeg and avconv will display any duration and the readout from -i shows as follows;

> avconv -i MrS-Feb09.mpg 
avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:12:07 with gcc 4.6.3
[mpeg2video @ 0x87985a0] mpeg_decode_postinit() failure
    Last message repeated 22 times
[mpegts @ 0x8793240] max_analyze_duration reached
[NULL @ 0x87ae660] start time is not set in estimate_timings_from_pts
[mpegts @ 0x8793240] PES packet size mismatch
    Last message repeated 1 times
Input #0, mpegts, from 'MrS-Feb09.mpg':
  Duration: N/A, start: 64760.806667, bitrate: N/A
  Program 4164 
    Metadata:
      service_name    : BBC ONE Lon
      service_provider: 
    Stream #0.0[0x65]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 29.65 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x66](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
    Stream #0.2[0x6a](eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s (visual impaired)
    Stream #0.3[0x69](eng): Subtitle: dvbsub
  Program 8261 
    Metadata:
      service_name    : ITV
      service_provider: 
    Stream #0.6[0x6a5]: Video: mpeg2video, 90k tbn
    Stream #0.5[0x6a6](eng): Audio: mp3, 0 channels
    Stream #0.4[0x6a7](eng): Audio: mp3, 0 channels (visual impaired)
    Stream #0.7[0x6c3](eng): Subtitle: dvbsub
At least one output file must be specified



I have tried using -t to remove the first few minutes but ffmpeg and avconv both report error, file cannot be read.

Any suggestions appreciated.

Geffers

---

### Post by FakeOutdoorsman on 2014-02-13
> I have tried using -t to remove the first few minutes but ffmpeg and avconv both report error, file cannot be read.

Please show the complete ffmpeg command and the complete console output.

---

### Post by Geoff_Lane on 2014-02-14
> **FakeOutdoorsman said:**
> Please show the complete ffmpeg command and the complete console output.

Here it is;



geoff@mercury:~/Desktop$ ffmpeg -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 90 MrS.mpg
ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg2video @ 0x91665a0] mpeg_decode_postinit() failure
    Last message repeated 22 times
[mpegts @ 0x9161240] max_analyze_duration reached
[NULL @ 0x917c660] start time is not set in estimate_timings_from_pts
[mpegts @ 0x9161240] PES packet size mismatch
    Last message repeated 1 times
Seems stream 6 codec frame rate differs from container frame rate: inf (1/0) -> -nan (0/0)
    Last message repeated 1 times
Input #0, mpegts, from 'MrS-Feb09.mpg':
  Duration: N/A, start: 64760.806667, bitrate: N/A
  Program 4164 
    Metadata:
      service_name    : BBC ONE Lon
      service_provider: 
    Stream #0.0[0x65]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 29.65 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x66](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
    Stream #0.2[0x6a](eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s (visual impaired)
    Stream #0.3[0x69](eng): Subtitle: dvbsub
  Program 8261 
    Metadata:
      service_name    : ITV
      service_provider: 
    Stream #0.6[0x6a5]: Video: mpeg2video, 90k tbn
    Stream #0.5[0x6a6](eng): Audio: mp3, 0 channels
    Stream #0.4[0x6a7](eng): Audio: mp3, 0 channels (visual impaired)
    Stream #0.7[0x6c3](eng): Subtitle: dvbsub
Output #0, mpeg, to 'MrS.mpg':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 15000 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: mp2, 48000 Hz, mono, 64 kb/s (visual impaired)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.2 -> #0.1
Press ctrl-c to stop encoding
frame=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbi[mpegts @ 0x9161240] Continuity check failed for pid 1701 expected 9 got 13
[mpegts @ 0x9161240] Continuity check failed for pid 1702 expected 1 got 14
[mpegts @ 0x9161240] Continuity check failed for pid 1703 expected 3 got 1
[mpegts @ 0x9161240] PES packet size mismatch
frame=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbi    Last message repeated 1 times
[mpegts @ 0x9161240] Continuity check failed for pid 1701 expected 2 got 4
[mpegts @ 0x9161240] Continuity check failed for pid 1702 expected 6 got 7
[mpegts @ 0x9161240] PES packet size mismatch
frame=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=    0 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbi    Last message repeated 4 times
frame=    0 fps=  0 q=-1.0 Lsize=       0kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead -nan%
geoff@mercury:~/Desktop$ 

Geffers

---

### Post by FakeOutdoorsman on 2014-02-14
Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) to format commands and console outputs so it is easier to read and easier to differentiate from your comments.

Try [downloading a recent build of the real ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds) and see if that works as expected:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
./ffmpeg -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 90 MrS.mpg
```

Notice the **./** before the **ffmpeg**.

---

### Post by siepo on 2014-02-16
Or you can install the original non-avconv ffmeg from the Severinsson ppa at [https://launchpad.net/~jon-severinsson/+archive/ffmpeg]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg") . I understand that, for compatibility reasons, these are not the latest versions.

All my troubles went away when I installed their packages, except for avidemux that I had to compile from source.

---

### Post by Geoff_Lane on 2014-02-16
I get the same error with avconv so is it still useful to try lastest ffmpeg?

Geffers

---

### Post by FakeOutdoorsman on 2014-02-16
Yes. Development of ffmpeg from FFmpeg is very active, and you may be experiencing an issue that has already been resolved.

---

### Post by Geoff_Lane on 2014-02-20
> **FakeOutdoorsman said:**
> Please use the [code tag]("http://ubuntuforums.org/misc.php?do=bbcode#code") to format commands and console outputs so it is easier to read and easier to differentiate from your comments.

Try [downloading a recent build of the real ffmpeg]("https://ffmpeg.org/download.html#LinuxBuilds") and see if that works as expected:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
./ffmpeg -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 90 MrS.mpg
```

Notice the **./** before the **ffmpeg**.

Tried that and got the following error;

```
[mpegts @ 0xabaf340] PES packet size mismatch
frame=    0 fps=0.0 q=-1.0 Lsize=       0kB time=00:00:00.00 bitrate=N/A    
video:0kB audio:0kB subtitle:0 data:0 global headers:0kB muxing overhead -nan%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)


```

This plays fine on my Sony Bravia TV's media player, how strange. Never had this problem with ffmpeg before.

Trouble is I need to replay it on a friend's media player and so far I have one device that can play it, the rest don't.

Geffers

---

### Post by FakeOutdoorsman on 2014-02-20
Please include your ffmpeg command and the complete console output.

---

### Post by Geoff_Lane on 2014-02-21
> **FakeOutdoorsman said:**
> Please include your ffmpeg command and the complete console output.

This is the total output using the latest ffmpeg you gave the link to.

```
geoff@mercury:~$ ./ffmpeg -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 120 MrS2.mpg
ffmpeg version N-60724-gb9936e5 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 19 2014 05:12:28 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 64.100 / 52. 64.100
  libavcodec     55. 52.102 / 55. 52.102
  libavformat    55. 33.100 / 55. 33.100
  libavdevice    55. 10.100 / 55. 10.100
  libavfilter     4.  1.102 /  4.  1.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
[mpeg2video @ 0xac951a0] Invalid frame dimensions 0x0.
    Last message repeated 22 times
[NULL @ 0xac96b80] start time is not set in estimate_timings_from_pts
[mpegts @ 0xac91340] PES packet size mismatch
    Last message repeated 1 times
[mpegts @ 0xac91340] Could not find codec parameters for stream 4 (Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels): unspecified frame size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0xac91340] Could not find codec parameters for stream 5 (Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels): unspecified frame size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0xac91340] Could not find codec parameters for stream 6 (Video: mpeg2video ([2][0][0][0] / 0x0002)): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, mpegts, from 'MrS-Feb09.mpg':
  Duration: N/A, start: 64760.806667, bitrate: N/A
  Program 4164 
    Metadata:
      service_name    : ?BBC ONE Lon
      service_provider: ?
  Program 8261 
    Metadata:
      service_name    : ?ITV
      service_provider: ?
    Stream #0:6[0x6a5]: Video: mpeg2video ([2][0][0][0] / 0x0002), 90k tbn
    Stream #0:5[0x6a6](eng): Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels
    Stream #0:4[0x6a7](eng): Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels (visual impaired)
    Stream #0:7[0x6c3](eng): Subtitle: dvb_subtitle ([6][0][0][0] / 0x0006)
  No Program
    Stream #0:0[0x65]: Video: mpeg2video (Main) ([2][0][0][0] / 0x0002), yuv420p(tv), 720x576 [SAR 64:45 DAR 16:9], max. 15000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0:1[0x66](eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, stereo, s16p, 248 kb/s
    Stream #0:2[0x6a](eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, mono, s16p, 62 kb/s (visual impaired)
    Stream #0:3[0x69](eng): Subtitle: dvb_subtitle ([6][0][0][0] / 0x0006)
Output #0, mpeg, to 'MrS2.mpg':
  Metadata:
    encoder         : Lavf55.33.100
    Stream #0:0: Video: mpeg2video ([2][0][0][0] / 0x0002), yuv420p, 720x576 [SAR 64:45 DAR 16:9], q=2-31, max. 15000 kb/s, 25 fps, 90k tbn, 25 tbc
    Stream #0:1(eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, stereo, 248 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
[mpegts @ 0xac91340] PES packet size mismatch
frame=    0 fps=0.0 q=-1.0 Lsize=       0kB time=00:00:00.00 bitrate=N/A    
video:0kB audio:0kB subtitle:0 data:0 global headers:0kB muxing overhead -nan%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)
geoff@mercury:~$ 


```

Geffers

---

### Post by FakeOutdoorsman on 2014-02-21
Try this:
```
./ffmpeg -analyzeduration 2G -probesize 2G -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 120 MrS2.mpg
```

Where did the input file come from and how was it created?

---

### Post by Geoff_Lane on 2014-02-21
> **FakeOutdoorsman said:**
> Try this:
```
./ffmpeg -analyzeduration 2G -probesize 2G -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 120 MrS2.mpg
```

Where did the input file come from and how was it created?

Set top box with HD. Box made by netgem, able to get files by USB or via network transfer.

No luck, this is the output;

```
geoff@mercury:~$ ./ffmpeg -analyzeduration 2G -probesize 2G -i MrS-Feb09.mpg -vcodec copy -acodec copy -ss 120 MrS2.mpg
ffmpeg version N-60724-gb9936e5 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 19 2014 05:12:28 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 64.100 / 52. 64.100
  libavcodec     55. 52.102 / 55. 52.102
  libavformat    55. 33.100 / 55. 33.100
  libavdevice    55. 10.100 / 55. 10.100
  libavfilter     4.  1.102 /  4.  1.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
[mpeg2video @ 0xba96220] Invalid frame dimensions 0x0.
    Last message repeated 22 times
[NULL @ 0xba97c20] start time is not set in estimate_timings_from_pts
[mpegts @ 0xba92380] PES packet size mismatch
    Last message repeated 1 times
[mpegts @ 0xba92380] Could not find codec parameters for stream 4 (Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels): unspecified frame size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0xba92380] Could not find codec parameters for stream 5 (Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels): unspecified frame size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
[mpegts @ 0xba92380] Could not find codec parameters for stream 6 (Video: mpeg2video ([2][0][0][0] / 0x0002)): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, mpegts, from 'MrS-Feb09.mpg':
  Duration: N/A, start: 64760.806667, bitrate: N/A
  Program 4164 
    Metadata:
      service_name    : ?BBC ONE Lon
      service_provider: ?
  Program 8261 
    Metadata:
      service_name    : ?ITV
      service_provider: ?
    Stream #0:6[0x6a5]: Video: mpeg2video ([2][0][0][0] / 0x0002), 90k tbn
    Stream #0:5[0x6a6](eng): Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels
    Stream #0:4[0x6a7](eng): Audio: mp3 ([4][0][0][0] / 0x0004), 0 channels (visual impaired)
    Stream #0:7[0x6c3](eng): Subtitle: dvb_subtitle ([6][0][0][0] / 0x0006)
  No Program
    Stream #0:0[0x65]: Video: mpeg2video (Main) ([2][0][0][0] / 0x0002), yuv420p(tv), 720x576 [SAR 64:45 DAR 16:9], max. 15000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0:1[0x66](eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, stereo, s16p, 248 kb/s
    Stream #0:2[0x6a](eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, mono, s16p, 62 kb/s (visual impaired)
    Stream #0:3[0x69](eng): Subtitle: dvb_subtitle ([6][0][0][0] / 0x0006)
Output #0, mpeg, to 'MrS2.mpg':
  Metadata:
    encoder         : Lavf55.33.100
    Stream #0:0: Video: mpeg2video ([2][0][0][0] / 0x0002), yuv420p, 720x576 [SAR 64:45 DAR 16:9], q=2-31, max. 15000 kb/s, 25 fps, 90k tbn, 25 tbc
    Stream #0:1(eng): Audio: mp2 ([3][0][0][0] / 0x0003), 48000 Hz, stereo, 248 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
[mpegts @ 0xba92380] PES packet size mismatch
frame=    0 fps=0.0 q=-1.0 Lsize=       0kB time=00:00:00.00 bitrate=N/A    
video:0kB audio:0kB subtitle:0 data:0 global headers:0kB muxing overhead -nan%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)
geoff@mercury:~$ 


```

Geffers

---

### Post by FakeOutdoorsman on 2014-02-22
Can you provide the input file? If it's huge perhaps you can use dd to shorten it if the smaller output also shows the same issue:
```
dd if=input.mpg of=output.mpg bs=1024 count=10000
```

---

### Post by Geoff_Lane on 2014-02-22
> **FakeOutdoorsman said:**
> Can you provide the input file? If it's huge perhaps you can use dd to shorten it if the smaller output also shows the same issue:
```
dd if=input.mpg of=output.mpg bs=1024 count=10000
```

Did you want me to just give the ff output for the new smaller file?

Geffers

---

### Post by FakeOutdoorsman on 2014-02-22
If you can upload the file somewhere that would be best. Dropbox, mediafire, and datafilehost all seem like decent file services if you need one, but I haven't used any of them in a long time.

---

### Post by Geoff_Lane on 2014-02-22
> **FakeOutdoorsman said:**
> Can you provide the input file? If it's huge perhaps you can use dd to shorten it if the smaller output also shows the same issue:
```
dd if=input.mpg of=output.mpg bs=1024 count=10000
```

Sorry, just read properly your reply so tried to attach the file but got 'invalid' file so zipped it then got 'Your file of 8.91 MB bytes exceeds the forum's limit of 976.6 KB for this filetype'. :(



Geffers

---

### Post by Geoff_Lane on 2014-02-22
> **FakeOutdoorsman said:**
> If you can upload the file somewhere that would be best. Dropbox, mediafire, and datafilehost all seem like decent file services if you need one, but I haven't used any of them in a long time.

For some reason I didn't think of that.

[https://dl.dropboxusercontent.com/u/72091535/MrS2.mpg?dl=1](https://dl.dropboxusercontent.com/u/72091535/MrS2.mpg?dl=1)

Geffers

---

