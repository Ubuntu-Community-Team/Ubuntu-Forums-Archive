---
title: "Audio ouf of sync with avconv"
date: 2015-02-05
forum: Multimedia Software
---

### Post by Schwarzer_Ritter on 2015-02-05
I try to record video with my Win TV capture card with avconv. The exact same lines worked fine with the exact same hardware with Ubuntu 12 and with SUSE (ffmpeg in this case), but with Ubuntu 14, the audio is out of sync.
> avconv -f video4linux2 -channel 1 -s 640x480 -i /dev/video0 -deinterlace -f alsa -i plughw:1,0 -ar 22050 -ab 64k -acodec ac3_fixed -vcodec mpeg4 -vb 2000k -y test.mp4

It will immedeately flood the terminal with "Non-monotonous DTS in output stream 0:1; previous: 20336, current: 20276; changing to 20337. This may result in incorrect timestamps in the output file" It cut the recording in the example off after a second.

> avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:19:26 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
-deinterlace is deprecated, use -filter:v yadif instead
[video4linux2 @ 0x9d877c0] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 18114.943674, bitrate: 92159 kb/s
    Stream #0.0: Video: rawvideo, yuv420p, 640x480, 92159 kb/s, 1000k tbn, 25 tbc
[alsa @ 0x9d88360] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9d88360] Estimating duration from bitrate, this may be inaccurate
Guessed Channel Layout for  Input Stream #1.0 : stereo
Input #1, alsa, from 'plughw:1,0':
  Duration: N/A, start: 18113.989693, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Output #0, mp4, to 'test.mp4':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Video: mpeg4, yuv420p, 640x480, q=2-31, 2000 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3_fixed, 22050 Hz, stereo, s16p, 64 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> mpeg4)
  Stream #1:0 -> #0:1 (pcm_s16le -> ac3_fixed)
Press ctrl-c to stop encoding
Non-monotonous DTS in output stream 0:1; previous: 20336, current: 20276; changing to 20337. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 20445, current: 20387; changing to 20446. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 20446, current: 20328; changing to 20447. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 20447, current: 20269; changing to 20448. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 20448, current: 19982; changing to 20449. This may result in incorrect timestamps in the output file.
^Cframe=   36 fps= 25 q=2.0 Lsize=      31kB time=1.44 bitrate= 174.4kbits/s    
video:15kB audio:14kB global headers:0kB muxing overhead 6.429734%
Received signal 2: terminating.

Of course, I tried to isolate the problem, by removing parts of the command. Recording video alone works fine, recording audio is the problem.
> avconv -f alsa -i plughw:1,0 -acodec ac3_fixed -y test.mp4
plughw:1,0 is the line if of my tv card, but it produces the same error, if I select the soundcard or webcam microphone.

> avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:19:26 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[alsa @ 0x95e2b40] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x95e2b40] Estimating duration from bitrate, this may be inaccurate
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, alsa, from 'plughw:1,0':
  Duration: N/A, start: 18501.989638, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Output #0, mp4, to 'test.mp4':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Audio: ac3_fixed, 48000 Hz, stereo, s16p, 192 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le -> ac3_fixed)
Press ctrl-c to stop encoding
Non-monotonous DTS in output stream 0:0; previous: -1744, current: -33439; changing to -1743. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1743, current: -31903; changing to -1742. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1742, current: -30367; changing to -1741. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1741, current: -28831; changing to -1740. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1740, current: -27295; changing to -1739. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1739, current: -26254; changing to -1738. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1738, current: -24718; changing to -1737. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1737, current: -23182; changing to -1736. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1736, current: -21646; changing to -1735. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1735, current: -20110; changing to -1734. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1734, current: -18574; changing to -1733. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1733, current: -17038; changing to -1732. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1732, current: -15502; changing to -1731. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1731, current: -13966; changing to -1730. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1730, current: -12430; changing to -1729. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1729, current: -10894; changing to -1728. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1728, current: -9358; changing to -1727. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1727, current: -7822; changing to -1726. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1726, current: -6286; changing to -1725. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1725, current: -4750; changing to -1724. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1724, current: -3214; changing to -1723. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1632, current: -2080; changing to -1631. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1631, current: -2029; changing to -1630. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:0; previous: -1630, current: -1982; changing to -1629. This may result in incorrect timestamps in the output file.
^Csize=      21kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:20kB global headers:0kB muxing overhead 4.147377%
Received signal 2: terminating.


---

