---
title: "How to change an MP4 to H.264/MPEG-4 AVC codec"
date: 2017-03-21
forum: Multimedia Software
---

### Post by oygle on 2017-03-21
This MP4 plays fine using VLC in Kubuntu, but doesn't play well (audio/video out of sync) on a Sony Bravia TV (via usb stick). Sometimes the video even slows right down, audio as well, so simply can't watch it. Found an article at [http://www.video-pedia.com/2016/03/30/play-mp4-files-on-bravia-tv-via-usb-drive/](http://www.video-pedia.com/2016/03/30/play-mp4-files-on-bravia-tv-via-usb-drive/) 

Seems the MP4 needs to be converted so that it is encoded with H.264/MPEG-4 AVC codec . Here is the video information ..

> ffmpeg version 2.8.11-0ubuntu0.16.04.1 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '******.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf56.40.101
  Duration: 01:17:47.72, start: 0.021333, bitrate: 4665 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 4525 kb/s, 50 fps, 50 tbr, 12800 tbn, 100 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 131 kb/s (default)
    Metadata:
      handler_name    : SoundHandler

How do I use ffmpeg to convert the MP4 to be encoded with H.264/MPEG-4 AVC codec please ?

---

### Post by TheFu on 2017-03-21
"mp4" is just a container and doesn't say what the audio or video codecs used are.

However, the easiest way to convert to know-working formats is to use Handbrake. It is a GUI tanscoding tool based on ffmepg.  [https://handbrake.fr/docs/en/latest/](https://handbrake.fr/docs/en/latest/) - use a PPA to load it.

---

### Post by oygle on 2017-03-21
> **TheFu said:**
> However, the easiest way to convert to know-working formats is to use Handbrake. It is a GUI tanscoding tool based on ffmepg.  [https://handbrake.fr/docs/en/latest/](https://handbrake.fr/docs/en/latest/) - use a PPA to load it.

Checked the codecs with ffmpeg and found this line ..

> DEV.LS h264                 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (decoders: h264 h264_crystalhd h264_vdpau ) (encoders: libx264 libx264rgb )

so I assume ffmpeg can do it; it's just a matter of getting the paramerts correct I assume. Handbrake is in synaptic, so I will install that and see how it goes.  Thanks

**Edit** - Handbrake is doing the encoding now, but it says the source codec is "h264" ?  So, maybe it is the TV that needs updates ? Anyway, I will let it finish, ..1 hr 40 mins, which is better than the 6 hrs yesterday on an old desktop (CPU was 98% ).

---

### Post by TheFu on 2017-03-21
Transcoding is CPU intensive. Not for a low-power system.  

Tried to transcode a 1080i show to 480p using an Atom CPU once - projected time was 48 hrs.  That same transcode on an i7 was 35 min.  I perform all transcoding on a Core i7 box since then ... or let Plex transcode whatever it is on a G3258 pentium as needed for my low-power players.

---

### Post by Bucky Ball on 2017-03-21
> **TheFu said:**
> However, the easiest way to convert to know-working formats is to use Handbrake. It is a GUI tanscoding tool based on ffmepg.  [https://handbrake.fr/docs/en/latest/](https://handbrake.fr/docs/en/latest/) - use a PPA to load it.

+1, but it's in the repos. No need for a PPA. Recently used repo version to do a heap of stuff. Faultless.

Use a package manager or 

```
sudo apt install handbrake
```

... should do it.

---

### Post by oygle on 2017-03-21
Thanks for your replies. The destination file from Handbrake was given a ".m4v" extension, and it wouldn't play on the TV. I will see how to make sure the TV has the latest updates.

Edit - Supported video file formats via USB are - [http://www.sony-asia.com/microsite/bravia_i-manuals/FY12/NX650/EN/usb_europe_ga_twn.html](http://www.sony-asia.com/microsite/bravia_i-manuals/FY12/NX650/EN/usb_europe_ga_twn.html)

---

### Post by TheFu on 2017-03-22
There are "presets" in handbrake. Pick one that should very popular, but isn't Apple. Verify that the container, a-codec, v-codec match what your TV can handle.  BTW, the TV seems VERY picky and doesn't list an Apple compatible file formats.

There are 1,000 different ways to solve this issue. Only you can pick the best answer for your unique situation.

Rather than deal with a picky TV, I spent $43 and got a Raspberry Pi device, loaded up Kodi, and never looked back. It isn't very picky about audio or video formats and can be networked. Plus, it can do more stuff when it isn't pushing video to be watched, like running a home nextcloud/email/pi-hole server.

Thousands of options.

The main reason I suggested the PPA, is that the repos are usually 1-2 yrs behind and for video software, that is usually way to far.

---

### Post by mc4man on 2017-03-22
Seems your tv wants MPEG4 part2, not MPEG4 part10. That type of encoding was typically seen in .avi but your tv specifies .mp4
In ffmpeg the encoder it would be -c:v mpeg4
If desired try this sample, quality is so-so to keep file size down (i.e. -qscale:v 7
Note files are rotated out from below so won't be there for extended time..
```
wget https://0x0.st/tnm.mp4 
```

encoding line for sample was,
ffmpeg -i  /home/doug/Videos/input.mkv  -c:v mpeg4 -qscale:v 7 -c:a copy out.mp4

---

### Post by Yellow Pasque on 2017-03-22
> **mc4man said:**
> Seems your tv wants MPEG4 part2, not MPEG4 part10.

It lists H.264/AVC inside an mpeg4 container as an option, though I think it's kind of confusing the way they list the format options.

---

### Post by Yellow Pasque on 2017-03-22
My only other thought is maybe the TV doesn't like 50fps:
```
Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 4525 kb/s, 50 fps, 50 tbr, 12800 tbn, 100 tbc (default)
```

---

### Post by mc4man on 2017-03-22
> **Temüjin said:**
> It lists H.264/AVC inside an mpeg4 container as an option, though I think it's kind of confusing the way they list the format options.
Who knows (that's why provided a sample.
It seemed to be laid out top to bottom as Extension ; Container ;  Video codec ; Audio codec which puts 
.m2ts / .mts > MPEG2TS >   AVC/H.264 
.mp4 >   MP4 > MPEG4 part2

---

