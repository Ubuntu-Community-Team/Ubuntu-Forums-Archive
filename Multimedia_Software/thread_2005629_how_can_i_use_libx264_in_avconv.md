---
title: "how can i use libx264 in avconv?"
date: 2012-06-17
forum: Multimedia Software
---

### Post by VdubVidiot on 2012-06-17
Can anyone please help me to learn how I can make my video output with libx264?
I am using ubuntu 12.4 LTE 64bit and I am a noob.:P

Thanks in advance.


avconv -i /home/brandon/Downloads/Sintel_1080.mkv -i /home/brandon/Downloads/sintel_trailer-audio.flac -c:v libx264 -pix_fmt yuv422p -g 0 -c:a pcm_s24le -t 44 108042230i.mov
avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
[matroska,webm @ 0x137c7a0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/home/brandon/Downloads/Sintel_1080.mkv':
  Metadata:
    ENCODER         : Lavf53.21.0
  Duration: 00:00:41.76, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 30 fps, 30 tbr, 1k tbn, 30 tbc (default)
[flac @ 0x1397580] max_analyze_duration reached
Input #1, flac, from '/home/brandon/Downloads/sintel_trailer-audio.flac':
  Duration: 00:00:52.00, bitrate: 721 kb/s
    Stream #1.0: Audio: flac, 48000 Hz, 2 channels, s16
[COLOR=Red]_Unknown encoder 'libx264'_[/COLOR]

---

### Post by VdubVidiot on 2012-06-18
the problem seems to have fixed itself after the following software removals and reinstallations:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219873&stc=1&d=1339999057[/IMG]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219874&stc=1&d=1339999057[/IMG]

---

### Post by OnOffPT on 2012-08-15
For me it worked fine installing libavcodec-extra-53.
[FONT="Courier New"]apt-get install libavcodec-extra-53[/FONT]

Run the following command before and after installing the libavcodec-extra-53 package:
[FONT="Courier New"]avconv -codecs | grep "264"[/FONT]

You should see a new line with libx264 as below
[FONT="Courier New"]avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10[/FONT]

---

### Post by ads52 on 2012-08-15
You might achieve better results with your encoding if you also use one of the x264 presets...

---

### Post by altendky on 2012-09-16
> **OnOffPT said:**
> For me it worked fine installing libavcodec-extra-53.

Worked for me...  thanks.  :]

---

### Post by RolPasto on 2012-11-06
It worked for me also. Thanks

---

