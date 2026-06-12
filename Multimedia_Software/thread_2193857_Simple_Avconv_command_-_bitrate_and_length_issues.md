---
title: "Simple Avconv command - bitrate and length issues"
date: 2013-12-15
forum: Multimedia Software
---

### Post by Sprakle on 2013-12-15
I try the following command:
```
avconv -i "Ashes.flac" "result.mp3"
```

Result:
[LIST]
[*]In Files, the bitrate is shown as 32K, and the length as 7:08 
[*]In Clementine (music player) the length is shown as 34:06, and seeking past 7:08 causes problems 
[*]From listening to the track I can tell the quality is much higher than 32K 
[/LIST]

Command output:
```

avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
[flac @ 0x1fa7d40] max_analyze_duration reached
Input #0, flac, from 'Ashes.flac':
  Metadata:
    TITLE           : Ashes
    ARTIST          : Aviators
    DATE            : 2013
    COMMENT         : Visit http://music.soundoftheaviators.com
    ALBUM           : Mirrors (Deluxe Version)
    track           : 6
    album_artist    : Aviators
    UNSYNCEDLYRICS  : {The song's lyrics}
  Duration: 00:07:08.68, bitrate: 1482 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, 2 channels, s32
Incompatible sample format 's32' for codec 'libmp3lame', auto-selecting format 's16'
Output #0, mp3, to 'result.mp3':
  Metadata:
    TIT2            : Ashes
    TPE1            : Aviators
    TDRL            : 2013
    COMMENT         : Visit http://music.soundoftheaviators.com
    TALB            : Mirrors (Deluxe Version)
    TRCK            : 6
    TPE2            : Aviators
    UNSYNCEDLYRICS  : {The song's lyrics}
    TSSE            : Lavf53.21.1
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (flac -> libmp3lame)
Press ctrl-c to stop encoding
size=   10049kB time=428.72 bitrate= 192.0kbits/s    
video:0kB audio:10048kB global headers:0kB muxing overhead 0.011935%

```

How can I fix this?

---

### Post by ajgreeny on 2013-12-15
Assuming your Ashes.flac file is not corrupt in any way leading to the wrong duration shown and the seek function failing on the mp3 you later made, you may need to set the output quality of the mp3 in the avconv command with something like ```
avconv -i Ashes.flac -acodec libmp3lame -aq 5 result.mp3
``` which should produce an mp3 file with a vbr of around 119Kbps.  You can change the bps output by using either a cbr in the command, eg, **-ab 196** or changing the quality figure to a lower figure, eg, **-aq 1** (higher output quality).

When I use that command on a long flac file it shows the full duration of 45+ minutes, so I wonder if your .flac is at fault in the first place.  Install **mediainfo** to see what that says about the source flac file; it may give us more clues.

---

### Post by Yellow Pasque on 2013-12-15
I find mp3val to be a useful tool in checking "correctness" of mp3's.

---

### Post by Sprakle on 2013-12-15
I tried changing the quality, but that didn't fix the problem.

To show what is happening, I created a simple 10 second flac file in Audacity, then converted it. Here are the results:
[ATTACH]248642[/ATTACH]

Since I know the file is not corrupted, and the command normally works for other people, could it be a dependency issue?

And the output:
```

ben@Ben-Ubuntu-Desktop:~/Software/Scripts/Nexus Sync/In$ avconv -i "Wawa.flac" -acodec libmp3lame -aq 5 "result.mp3"
avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
[flac @ 0x1717d40] max_analyze_duration reached
Input #0, flac, from 'Wawa.flac':
  Duration: 00:00:10.00, bitrate: 378 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, 1 channels, s16
Output #0, mp3, to 'result.mp3':
  Metadata:
    TSSE            : Lavf53.21.1
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 1 channels, s16, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (flac -> libmp3lame)
Press ctrl-c to stop encoding
size=      90kB time=10.03 bitrate=  73.4kbits/s    
video:0kB audio:90kB global headers:0kB muxing overhead 0.149150%

```

---

### Post by ajgreeny on 2013-12-16
The output you show is almost identical the what I see when I do the exact same conversion of your Wawa.flac file to results.mp3, but with very minor differences.
Here's my terminal output; note I am running 12.04 with a slightly earlier version of avconv than you used.
```
avconv -i Wawa.flac -acodec libmp3lame -aq 5 file.mp3
avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
[flac @ 0x176e9a0] max_analyze_duration reached
Input #0, flac, from 'Wawa.flac':
  Duration: 00:00:10.00, bitrate: 378 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, 1 channels, s16
Output #0, mp3, to 'file.mp3':
  Metadata:
    TSSE            : Lavf53.21.1
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 1 channels, s16, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (flac -> libmp3lame)
Press ctrl-c to stop encoding
size=      91kB time=10.03 bitrate=  74.1kbits/s    
video:0kB audio:91kB global headers:0kB muxing overhead 0.147610%
``` I'm not sure I can help any more on this, but good luck.

---

### Post by FakeOutdoorsman on 2013-12-16
This is known as a **YALB**: Yet Another Libav Bug.

Using a [recent build of ffmpeg from FFmpeg](http://ffmpeg.org/download.html#LinuxBuilds):
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input.flac -c:a libmp3lame -q:a 5 output.mp3
```

Clementine screenshot (13.04):
[ATTACH=CONFIG]248659[/ATTACH]

```

./ffmpeg -i Wawa.flac -b:a 32k ba.mp3
avconv -i Wawa.flac -b:a 32k ba-avconv.mp3
./ffmpeg -i Wawa.flac -f wav pipe: | lame - lame.mp3
./ffmpeg -i Wawa.flac -f wav pipe: | lame -b 32 - lameb.mp3
./ffmpeg -i Wawa.flac -q:a 5 qa.mp3
avconv -i Wawa.flac -q:a 5 qa-avconv.mp3
```

---

