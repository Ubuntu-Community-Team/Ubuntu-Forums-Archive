---
title: "How to get the mediainfo of a video from terminal?"
date: 2015-03-21
forum: Multimedia Software
---

### Post by remmas-sido on 2015-03-21
Hello guys 
Is there a way I can get the mediainfo of a video displayed in the terminal?
Thank you

---

### Post by ron998 on 2015-03-21
> **remmas-sido said:**
> ...Is there a way I can get the mediainfo of a video displayed in the terminal?
Yes, use mediainfo with command line...
```
mediainfo filename
```
> [SIZE=1]@xubuntu:~$ mediainfo filename.mp4
General
Complete name                            : filename.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 1.57 MiB
Duration                                 : 30s 66ms
Overall bit rate                         : 439 Kbps
Writing application                      : Lavf56.26.101

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L2.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 8 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 30s 66ms
Bit rate                                 : 380 Kbps
Width                                    : 512 pixels
Height                                   : 288 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 14.967 fps
Original frame rate                      : 15.000 fps
Minimum frame rate                       : 7.463 fps
Maximum frame rate                       : 15.152 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.172
Stream size                              : 1.33 MiB (84%)
Writing library                          : x264 core 79
Encoding settings                        : cabac=1 / ref=8 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=6 / psy=1 / psy_rd=1.0:0.0 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=3 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=2 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=0 / wpredp=2 / keyint=150 / keyint_min=15 / scenecut=40 / rc_lookahead=40 / rc=abr / mbtree=1 / bitrate=380 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Color primaries                          : BT.601 NTSC
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.601

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 29s 954ms
Bit rate mode                            : Constant
Bit rate                                 : 64.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 234 KiB (15%)[/SIZE]

---

### Post by Holger_Gehrke on 2015-03-21
Or -- if you've got mplayer installed -- the script /usr/share/mplayer/midentify.sh

---

### Post by FakeOutdoorsman on 2015-03-21
ffprobe is another option and what I prefer to use for getting info. It has a learning curve, but it supports several output formatting types and you can choose to output specific info which can then be used in scripts.

Show info about the container format and the streams:
```
ffprobe -show_format -show_streams input.mp4
```

Example to get the duration in seconds:
```
$ ffprobe -v error -show_entries format=duration -of default=nokey=1:noprint_wrappers=1 input.mkv
5010.113000
```

Same thing, but in HOURS:MM:SS.MICROSECONDS format:
```
$ ffprobe -v error -show_entries format=duration -sexagesimal -of default=nokey=1:noprint_wrappers=1 input.mkv
1:23:30.113000
```

See the [FFprobe Documentation](https://ffmpeg.org/ffprobe.html) and [FFmpeg Wiki: FFprobe Tips](http://trac.ffmpeg.org/wiki/FFprobeTips) for more info and examples.

It's not available in the repos yet. You can get a recent [static build of ffprobe](http://johnvansickle.com/ffmpeg/), [compile ffprobe](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), or use [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).

---

### Post by mc4man on 2015-03-21
I like ffprobe here also in some cases, as far as mediainfo generally just use the gui. From the command line it can be quite extensive if such stuff is needed or desired.
(- to see *some* just run this, outputting to file in Home folder as it's 1300+ lines
```
mediainfo --Info-Parameters > mediainfo.txt
```

---

### Post by remmas-sido on 2015-03-23
> **ron998 said:**
> Yes, use mediainfo with command line...
```
mediainfo filename
```
I did cd /home/remmas/Desktop/ 
which means I acces the video directory using the cd command after I type ls to display the content of my desktop 
/Desktop$ ls
BLUETOOTH  [HorribleSubs] Strike the Blood - 01 [1080p].mkv

there is a folder named "BLUETOOTH" and a video named "[HorribleSubs] Strike the Blood - 01 [1080p].mkv"
 when I type mediainfo [HorribleSubs] Strike the Blood - 01 [1080p].mkv here is what displayed
 remmas@remmas-Inspiron-1545:~/Desktop$ 
is there something I missed, sorry if the reply is a little bit messy.

> **FakeOutdoorsman said:**
> ffprobe is another option and what I prefer to use for getting info. It has a learning curve, but it supports several output formatting types and you can choose to output specific info which can then be used in scripts.

Show info about the container format and the streams:
```
ffprobe -show_format -show_streams input.mp4
```

Example to get the duration in seconds:
```
$ ffprobe -v error -show_entries format=duration -of default=nokey=1:noprint_wrappers=1 input.mkv
5010.113000
```

Same thing, but in HOURS:MM:SS.MICROSECONDS format:
```
$ ffprobe -v error -show_entries format=duration -sexagesimal -of default=nokey=1:noprint_wrappers=1 input.mkv
1:23:30.113000
```

See the [FFprobe Documentation]("https://ffmpeg.org/ffprobe.html") and [FFmpeg Wiki: FFprobe Tips]("http://trac.ffmpeg.org/wiki/FFprobeTips") for more info and examples.

It's not available in the repos yet. You can get a recent [static build of ffprobe]("http://johnvansickle.com/ffmpeg/"), [compile ffprobe]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"), or use [mc4man's PPA]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media").

Do you mind telling me the way you installed?

---

### Post by SeijiSensei on 2015-03-23
The shell treats spaces as delimiters.  If you have a file with embedded spaces in its name, encase it in single quotes like this:
```
mediainfo 'file name with spaces.mkv'
```
Also I suggest that including the file names of illegally-obtained content in your postings is not a good idea.

---

### Post by Yellow Pasque on 2015-03-23
> If you have a file with embedded spaces in its name, encase it in single quotes
..or learn how to use auto-complete like the rest of us lazy typists.

---

### Post by SeijiSensei on 2015-03-23
> **Temüjin said:**
> ..or learn how to use auto-complete like the rest of us lazy typists.
Just so the OP knows what you mean, you can type a few characters from the beginning of the name and press the Tab key.  You'll get this:
```
mediainfo file\ with\ spaces\ in\ name.mkv
```
where the space characters are "escaped" by the backslash character.  That tells the shell to treat a space as a character, not a delimiter.  You can, of course, type the backslashes yourself, or just wrap the string in quotes as I mentioned before.

---

### Post by FakeOutdoorsman on 2015-03-23
> **remmas-sido said:**
> Do you mind telling me the way you installed?

I don't use Ubuntu. If I did I would compile, but most users don't need to do that unless they want to tweak it.

Downloading the static build is easy. Just download, extract, and run. No installing needed. Or the PPA is easy. Probably something like this:

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install ffmpeg
```

I believe this package includes ffprobe.

---

### Post by mc4man on 2015-03-24
> **FakeOutdoorsman said:**
> I don't use Ubuntu. If I did I would compile, but most users don't need to do that unless they want to tweak it.

Downloading the static build is easy. Just download, extract, and run. No installing needed. Or the PPA is easy. Probably something like this:

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install ffmpeg
```

I believe this package includes ffprobe.
For ffmpeg that would be ok though in general the ppa needs this one time as some sources have newer package names  - 
```
sudo apt-get dist-upgrade
```
There are also some warnings that I try to make obvious (top & bottom of page, bottom of terminal) so usually best to go there [first & read]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")

---

### Post by FakeOutdoorsman on 2015-03-24
I'm forgetting how to use Ubuntu.

---

### Post by Yellow Pasque on 2015-03-24
> **FakeOutdoorsman said:**
> I'm forgetting how to use Ubuntu.

FakeUbuntuman? Heh, that's okay. I've been running Debian sid as my main distro for 3-4 years now (primarily using xfce). I often feel the same way, especially when it comes to Unity.

---

### Post by shantiq on 2015-04-05
also found this recently which I did not know existed;   much data given


**then re-read the OP question and saw it was for video not audio ....    will leave this here for reference anyway :]**

SoX must be installed first so    ```
sudo apt-get install sox libsox-fmt-all
```    and then to run

```
soxi -V nameoffile.whateveraudiocodec

```
```
**soxi -V  ***soxi INFO formats: detected file format type `flac'


Input File     : '01 - erik satie - cinema entr'acte symphonique de relache.flac'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:18:31.68 = 49025088 samples = 83376 CDDA sectors
File Size      : 93.3M
Bit Rate       : 672k
Sample Encoding: 16-bit FLAC
Comments       : 
ALBUM=Musique D'ameublement, Vexations, Concertpiece for Trautonium & Strings (Marius Constant, Munich Chamber Orchestra)
ALBUMARTIST=Erik Satie & Paul Hindemith
ARTIST=Erik Satie
COMPOSER=Erik Satie
DATE=2006
GENRE=Classical
GENRE=Electronic
ISRC=FRZ200300124
LABEL=Apex
LABEL=Warner Classics
STYLE=Modern
STYLE=Contemporary
STYLE=Minimal
TITLE=Cinéma entr'acte symphonique de Relâche
TRACKTOTAL=9
TRACKNUMBER=1
replaygain_album_gain=+3.94 dB
replaygain_album_peak=0.939056
replaygain_track_gain=+2.66 dB
replaygain_track_peak=0.913330



```

---

