---
title: "avconv creates idioticly huge but broken files..."
date: 2014-09-12
forum: Multimedia Software
---

### Post by sgofferj on 2014-09-12
Hi,

I have just tried to run my old ffmpeg mass-conversion script with avconv and it produces idioticly large files which vlc reports as being broken. Vlc does play them but the quality is more than bad.
Anybody knows what exactly is different in avconv? That's my commandline:

avconv -i "${filename}" -vcodec libxvid -s 624x352 -aspect 16:9 -b:v 1200k -acodec libmp3lame -b:a 128k "${barename}.avi"

The commandline runs through a loop which converts all camera-h264 files in a diectory to xvid so I can watch them with my network media player

-S

---

### Post by andrew.46 on 2014-09-12
Could you run the command on a single file and then post the full command and complete terminal output here?

---

### Post by papibe on 2014-09-12
Hi sgofferj.

According to the avconv (Libav) [documentation]("https://libav.org/faq.html#How-do-I-encode-Xvid-or-DivX-video-with-avconv_003f") you should use mpeg4 as codec and tag it as 'xvid'.

This works for me on a 12.04 server:
```
avconv -y -i "$source" \
        -c:v mpeg4 \
        -vtag xvid \
        -s 624x352 -aspect 16:9 \
        -b:v 1200k \
        -c:a libmp3lame \
        -b:a 128k \
        -ac 2 \
        "$output"

```
Hope it helps. Let us know if that works better for you.
Regards.

---

### Post by sgofferj on 2014-09-12
I tried the exact code above now with a 52 minutes, 347MB h.264 file and I get a 2.1GB avi out of it... With ffmpeg on Opensuse, the same conversion gets me a 500-something MB avi.

```
sgofferj@nostromo:/storage/public/todo$ h264toxvidmp3.sh 
avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:16:02 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'camera1-2014-06-02.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2014-06-02 01:58:08
  Duration: 00:52:20.80, start: 0.000000, bitrate: 884 kb/s
    Stream #0.0(und): Audio: aac, 48000 Hz, stereo, fltp, 124 kb/s
    Metadata:
      creation_time   : 2014-06-02 01:58:08
    Stream #0.1(und): Video: h264 (High), yuv420p, 720x404, 756 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2014-06-02 01:18:31
Output #0, avi, to 'camera1-2014-06-02.avi':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2014-06-02 01:58:08
    ISFT            : Lavf54.20.4
    Stream #0.0(und): Video: mpeg4, yuv420p, 624x352 [PAR 255:254 DAR 9945:5588], q=2-31, 1200 kb/s, 24k tbn, 24k tbc
    Metadata:
      creation_time   : 2014-06-02 01:18:31
    Stream #0.1(und): Audio: libmp3lame, 48000 Hz, stereo, fltp, 128 kb/s
    Metadata:
      creation_time   : 2014-06-02 01:58:08
Stream mapping:
  Stream #0:1 -> #0:0 (h264 -> mpeg4)
  Stream #0:0 -> #0:1 (aac -> libmp3lame)
Press ctrl-c to stop encoding
frame=75302 fps= 99 q=6.3 Lsize= 2019268kB time=3140.68 bitrate=5267.0kbits/s    
video:200447kB audio:49074kB global headers:0kB muxing overhead 709.257320%

```

---

### Post by papibe on 2014-09-12
Does VLC still report the file as broken?

In my experience, conversion from a h264 to an xvid avi will always produce a bigger file.

Although I can't comment in the effectiveness of ffmpeg vs. avconv, I know you can install proper ffmpeg on Ubuntu. There is a guide on the forum somewhere, and in the FFmpeg site too.

Let us know if you need more details on that.

Regards.

---

### Post by sgofferj on 2014-09-12
Jup, file is still broken. I know that mpeg4/xvid is bigger than h.264. The 500-something MB is pretty much what I would expect, but 2.1GB is ridiculous. Additionally, when I play the file, it shows tons of compression artefacts, so it's totally messed up. It looks pretty muc like avconv is broken here. I already noticed that conversion from h.264 to DNxHD produces trash in high contrast areas...
I wonder why Ubuntu is using avconv when it's that immature...

---

### Post by sgofferj on 2014-09-12
Found something interesting... Look what my Opensuse ffmpeg says for the output:
  Stream #0:0(und): Video: mpeg4 (xvid / 0x64697678), yuv420p, 624x352 [SAR 255:254 DAR 9945:5588], q=2-31, 1200 kb/s, SAR 352:351 DAR 16:9, 23.98 tbn, 23.98 tbc (default)
And in comparison avconv
  Stream #0.0(und): Video: mpeg4, yuv420p, 624x352 [PAR 255:254 DAR 9945:5588], q=2-31, 1200 kb/s, 24k tbn, 24k tbc

24_***k***_ tbn/tbc?! Boy, this is messed up...

Also, ffmpeg is almost double as fast (180fps vs. 110fps avconv) and that although ffmpeg accesses the files via NFS...

---

### Post by andrew.46 on 2014-09-12
It all sounds a little odd... Perhaps if you are keen on aiming at a specific bitrate rather than a video 'quality' setting you could experiment with a 2 pass encode.

---

### Post by mc4man on 2014-09-12
> I tried the exact code above now with a 52 minutes, 347MB h.264 file and I get a 2.1GB avi out of it
> bitrate=5267.0kbits/s
That would seem to be about right. The question is why is it encoding at that bitrate

While I use FFmpeg here for encoding a quick test between ffmpeg 2.3.3  & avconv 11 show that both produce virtually the same file using the parameters you posted

avconv - 
Video
ID                                       : 0
Format                                   : xvid
Codec ID                                 : xvid
Duration                                 : 2mn 15s
Bit rate                                 : 1 193 Kbps
Width                                    : 624 pixels
Height                                   : 352 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Bits/(Pixel*Frame)                       : 0.181
Stream size                              : 19.2 MiB (89%)

ffmpeg
Video
ID                                       : 0
Format                                   : xvid
Codec ID                                 : xvid
Duration                                 : 2mn 15s
Bit rate                                 : 1 191 Kbps
Width                                    : 624 pixels
Height                                   : 352 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Bits/(Pixel*Frame)                       : 0.181
Stream size                              : 19.2 MiB (89%)

with the mp3 audio comes out to 1335 & 1333  Kbps respectively

---

### Post by sgofferj on 2014-09-13
> **mc4man said:**
> That would seem to be about right. The question is why is it encoding at that bitrate
Jup, good question! As you can see from the output, it does understand that I specified 1200k bitrate. But in the same category falls the question why it thinks it should use tbn/tbc of 24k instead of 23.98 without the "k"...

> While I use FFmpeg here for encoding a quick test between ffmpeg 2.3.3  & avconv 11 show that both produce virtually the same file using the parameters you posted
Which leads me again to the assumption that the avconv which comes with Ubuntu 14.04 (9.16-6:9.16-0ubuntu0.14.04.1) is broken... At least I didn't do anything fancy. That machine (my new core and storage server) is set up pretty freshly and all is stock, i.e. no self-compiled stuff.

---

### Post by sgofferj on 2014-09-14
Where does one reports bugs for Ubuntu? The video-rendering stuff is close to a dealbreaker for me, especially as avconv seems to have further bugs (s. [https://forum.kde.org/viewtopic.php?f=272&t=122583](https://forum.kde.org/viewtopic.php?f=272&t=122583)) and I'm considering ending my Ubuntu experiments and returning to Opensuse.

---

### Post by mc4man on 2014-09-14
To file a bug one goes ubuntu-bug packagename though you'll need a launchpad account to actually file. (ubuntu-bug libav-tools
If your issue is just avconv then try using ffmpeg instead, there are various ways to install. (build, use a pre-compiled binary, various ppa's
(a quick test here suggests mlt will use ffmpeg over avconv if ffmpeg is in path, otherwise can be configured to do so. 
If your issues extend further than that then maybe opensuse is better option

If you wish to try a newer mlt & avconv for 14.04 then take a [look here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6") , though I've somewhat intended that ppa to be used along with [this one]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")
(i may  decide to go with FFmpeg shared with the next FFmpeg release instead of libav11, may not..

---

### Post by sgofferj on 2014-09-14
Thanks, I'll check and test.

---

