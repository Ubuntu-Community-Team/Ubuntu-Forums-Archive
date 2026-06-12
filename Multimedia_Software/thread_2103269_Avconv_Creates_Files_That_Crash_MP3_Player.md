---
title: "Avconv Creates Files That Crash MP3 Player"
date: 2013-01-09
forum: Multimedia Software
---

### Post by AvoidedRider on 2013-01-09
I have been trying to create MP3 files using a Thunar custom action  under Xubuntu.  The command that I was using in the custom action was as  follows.
```
xfce4-terminal -x  ffmpeg -i %f -acodec libmp3lame -v 8 New/%n.mp3
```This  has the obvious issue of I haven't figured out the sed command to strip  the various file types that I might have selected. Much less obvious  and much more important is that when I transfered the files to my MP3  player the player essentially locked up and died. So after some  irritation and blaming the MP3 manufacturer I found out that some files  worked and other didn't. Depending on what software I use I get  different answers. Rythmbox tells me that nothing is wrong that they  files are whatever kbps similar to my conversion software. Thunar tells  me that every file that is crashing is 32 KBit/s. VLC has confused  answer. Under media information codec tab it says that
>  codec: MPEG Audio Layer 1/2/3 (mpga)
Channels: Stereo
Sample Rate: 44100 Hz
Bitrate: 32 kb/s but on the statistics tab
it  says under input/read that the content bitrate is whatever it is  supposed to be. Also for reference under the  metadata  tab on files  that don't work it says among other things
> major_brand: mp42
compatible_brands: mp42isom3gp63g2a3gp4
minor_version: 0On ones that work it says nothing on that tab or Software: Lavf52.64.2

Using  WinFF or ffmpeg result in the same issue. If I use VLC to convert/save I  get a good file. However it seems like using that to convert every file  in my library would take a little bit of time. I am hoping to be able  to select files and send them to a new folder with a simple right click.

---

### Post by ajgreeny on 2013-01-09
To get info about the files you've made you could try simply running ```
ffmpeg -i file.mp3
```With no output file it will simply report the file details and may give you a clue.  You can use the same command but with avconv instead of ffmpeg.

For even more detailed file info install mediainfo and run ```
mediainfo -l file.mp3
```I seem to remember mediainfo is available from a ppa, not the standard repos, but I may be wrong about that.

---

### Post by AvoidedRider on 2013-01-10
First file is one of the bad files created using Avconv and the second is a good file done with VLC

> craig@TheSleeper:/media/SANSA CLIPZ/PODCASTS/MUSIC$ avconv -i ZEA.mp3
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
[mp3 @ 0x10e89c0] max_analyze_duration reached
Input #0, mp3, from 'ZEA.mp3':
  Metadata:
    title           : Watch Out!!
    artist          : ZEA
    minor_version   : 0
    compatible_brands: mp42isom3gp63g2a3gp4
    major_brand     : mp42
    creation_time   : 2012-06-17T20:06:48
    encoder         : Lavf53.21.0
  Duration: 00:03:09.75, start: 0.000000, bitrate: 77 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 32 kb/s
At least one output file must be specified
> craig@TheSleeper:/media/SANSA CLIPZ/PODCASTS/MUSIC$ mediainfo -l ZEA.mp3
General
Complete name                            : ZEA.mp3
Format                                   : MPEG Audio
File size                                : 1.76 MiB
Duration                                 : 3mn 9s
Overall bit rate mode                    : Variable
Overall bit rate                         : 77.6 Kbps
Track name                               : Watch Out!!
Performer                                : ZEA
Encoded date                             : UTC 2012-06- 7T20:06:48
Writing library                          : LAME3.99
Encoding settings                        : Lavf53.21.0
minor_version                            : 0
compatible_brands                        : mp42isom3gp63g2a3gp4
major_brand                              : mp42

Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Duration                                 : 3mn 9s
Bit rate mode                            : Variable
Bit rate                                 : 77.6 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 1.75 MiB (100%)
Writing library                          : LAME3.99> craig@TheSleeper:/media/SANSA CLIPZ/PODCASTS/MUSIC$ avconv -i kira.mp3
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
[mp3 @ 0xae39c0] max_analyze_duration reached
[mp3 @ 0xae39c0] Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'kira.mp3':
  Duration: 00:03:15.99, start: 0.000000, bitrate: 127 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
At least one output file must be specified> craig@TheSleeper:/media/SANSA CLIPZ/PODCASTS/MUSIC$ mediainfo -l kira.mp3General
Complete name                            : kira.mp3
Format                                   : MPEG Audio
File size                                : 2.99 MiB
Duration                                 : 3mn 15s
Overall bit rate mode                    : Constant
Overall bit rate                         : 128 Kbps
Writing library                          : LAME3.99.3

Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Duration                                 : 3mn 16s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 2.99 MiB (100%)
Writing library                          : LAME3.99.3

---

### Post by ajgreeny on 2013-01-11
The biggest difference I can see is the 
> Encoding settings                        : Lavf53.21.0
minor_version                            : 0
compatible_brands                        : mp42isom3gp63g2a3gp4
major_brand                              : mp42
section in the info for the bad file that is not showing in the good file, along with a different bitrate value; the good file is constant at 128, the bad variable at 77.6.

Unfortunately I have no idea what it all means, or even if it's important, but it may give you a start for further searching, though google does not help me with that at all.

---

### Post by AvoidedRider on 2013-01-11
None of my searches of the internet provided anything useful either and I have been looking for a few months now.  The most important thing that I see is> Duration: 00:03:09.75, start: 0.000000, bitrate: 77 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 32 kb/s
I am not sure if it is a tag related issue or not but all efforts to rewrite the tags hasn't helped. Using a constanst bit rate still left the one value for the bit rate stuck at 32 kb/s.

---

### Post by AvoidedRider on 2013-03-02
In case anyone stumbles into this page looking for an answer to a similar problem I was able to find a workaround. By using Audacity I am able to get working useful files. Unfortunately I have not found a way to set this program up to work with custom actions and it has a habit of crashing but it works.

---

### Post by FakeOutdoorsman on 2013-03-02
What player is it?

I've seen this (or a similar issue) before, and the user resolved it by using real ffmpeg (the version from the repo is not from FFmpeg). I recommend trying a recent [static build of ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds). No need to install. Just download the archive, extract, and then run the binary: ([example](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)). I don't know if it will work for you, but it is worth a try.

---

### Post by andrew.46 on 2013-03-02
Could you post one of the broken mp3 files online? Here might be a good spot:

[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by AvoidedRider on 2013-03-04
For diagnostic purposes I put a copy of a file that is bad online at the following location.
[https://www.dropbox.com/s/km92w7c2j9cfoej/One.mp3?m](https://www.dropbox.com/s/km92w7c2j9cfoej/One.mp3?m)
The mp3 player is a SanDisk sansa Clip Zip.
I will try the static build of ffmpeg mentioned later tonight and see if it gives me any better results.

---

### Post by AvoidedRider on 2013-03-04
Ok I gave that a try and it seems to be working. There is still some disagreement between devices on the bit rate of the file but it is playing on the device.  I used the -v 8 option and it is reporting it as a 56 Kbps fixed rate. Thunar properties concur and vlc shows that the codec bitrate is 56 kb/s while the file input bitrate is 132 kb/s.

So are we saying that```
sudo apt-get install ffmpeg
``` is not the correct way to install this program?

Here is the output from the ffprobe program.
```
 ./ffprobe -i one1.mp3
ffprobe version N-50389-ge20f2dc Copyright (c) 2007-2013 the FFmpeg developers
  built on Mar  1 2013 05:11:34 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 17.103 / 52. 17.103
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.102 / 54. 63.102
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 41.100 /  3. 41.100
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[mp3 @ 0x98297c0] max_analyze_duration 5000000 reached at 5015510 microseconds
Input #0, mp3, from 'one1.mp3':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isom3gp63g2a3gp4
    encoder         : Lavf54.63.102
  Duration: 00:02:49.22, start: 0.000000, bitrate: 128 kb/s
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, s16p, 128 kb/s


```

---

### Post by andrew.46 on 2013-03-05
> **AvoidedRider said:**
> For diagnostic purposes I put a copy of a file that is bad online at the following location.
[https://www.dropbox.com/s/km92w7c2j9cfoej/One.mp3?m](https://www.dropbox.com/s/km92w7c2j9cfoej/One.mp3?m)


File plays fine here, it is vbr which might account for the varying results with players interrogating it...

---

### Post by FakeOutdoorsman on 2013-03-05
> **AvoidedRider said:**
> There is still some disagreement between devices on the bit rate of the file but it is playing on the device.  I used the -v 8 option and it is reporting it as a 56 Kbps fixed rate. Thunar properties concur and vlc shows that the codec bitrate is 56 kb/s while the file input bitrate is 132 kb/s.

You can calculate the average bitrate manually. A 3 MB file that has a duration of 4 minutes would be:
```
(3 MB * 8192) / 240 seconds = 102.4 kilobits/second
```

> **AvoidedRider said:**
> So are we saying that```
sudo apt-get install ffmpeg
``` is not the correct way to install this program?
Correct. See:
[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

---

### Post by perchecreek on 2013-03-18
I can confirm this problem -- mp3s created from flvs with ubuntu's version of ffmpeg were unplayable on a SanDisk Clip+. I used ffmpeg -i $i -ab 192k -ar 44100 $i.mp3, and also avconv -i $i -ab 192k -ar 44100 $i.mp3, and playing mp3s so created froze the player. I replaced /usr/bin/ffmpeg with the ffmpeg static binary downloaded from the link provided in post #7 in this thread, converted same flv files to mp3s, and they now play without freezing. I'm using Mint 13 Maya. I routinely use ffmpeg, and this problem just appeared within the last week or three, so perhaps there was a change to ubuntu's version of ffmpeg that broke something. I had also arrived at the solution of converting flv to mp3 with Audacity, which produced mp3s that worked.

---

