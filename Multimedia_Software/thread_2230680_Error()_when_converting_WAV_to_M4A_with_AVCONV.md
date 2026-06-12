---
title: "Error(?) when converting WAV to M4A with AVCONV"
date: 2014-06-20
forum: Multimedia Software
---

### Post by sir-marky on 2014-06-20
I have ripped some songs from a CD to wav files with the command,   
```


cdparanoia -vB


```
 
I then convert these wav files to ALAC format with the command, 

  ```
for f in ./*.wav; do avconv -i "$f" -c:a alac "${f%.*}.m4a"; done

```  The following message is an example displayed at the end of each container conversion with the error in yellow text.

  ```
avconv version 9.13-6:9.13-0ubuntu0.14.04.1+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on May 10 2014 17:26:31 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
[wav @ 0x1cde840] [COLOR=#ffa500]max_analyze_duration reached
Guessed Channel Layout for  Input Stream #0.0 : stereo[/COLOR]
Input #0, wav, from './15 - Eels - Mr E's Beautiful Blues.wav':
  Duration: 00:03:58.53, bitrate: 1411 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Output #0, ipod, to './15 - Eels - Mr E's Beautiful Blues.m4a':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Audio: alac, 44100 Hz, stereo, s16p, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le -> alac)
Press ctrl-c to stop encoding
size=   26984kB time=238.61 bitrate= 926.4kbits/s    
video:0kB audio:26964kB global headers:0kB muxing overhead 0.076887%
markrich@markys-home-pc:/btrfs/music/iTunes/Temp/Eels - Daisies Of The Galaxy$ 


```  The M4a files do play, however some have the occasional artefacts  within them that give the impression of those old fashioned LP things.
  Can anyone suggest what I am doing wrong?
  
Using Ubuntu 14.04

  CDParanoia III, release 10.2
  AVCONV, version 9.13-6:9.13-0ubuntu0.14.04.1+fdkaac

---

### Post by andrew.46 on 2014-06-22
Can you:

[LIST=1]
[*]Post the full command + complete terminal output from one of these conversions
[*]Post a sample of one of the troublesome files, perhaps [here...]("http://www.datafilehost.com/")
[*]
[/LIST]

Thanks :)

---

### Post by sir-marky on 2014-06-22
The full commands are above.

---

### Post by mc4man on 2014-06-22
I don't believe the 2 messages are your issue, avconv shows that when inputting .wav (both libav9 & 10
FFmpeg is similar though it only will show the later message,  "Guessed Channel Layout for  Input Stream #0.0 : stereo"
(in a default gnome-terminal red is an error, yellow just an info message

If desired you could install ffmpeg & see. (avail. from same ppa as a binary only install), just replace avconv in command with ffmpeg

Other option could be to use something like rubyripper to rip & encode to alac (will also tag if desired
discussed [here]("http://ubuntuforums.org/showthread.php?t=1533534&page=2"),  the 'other' command could be either avconv or ffmpeg if installed
The 'other' command could also be modernized to -c:a alac from -acodec alac

Not mentioned in that thread is for neroAac* to work on 64 bit one needs to install lib32stdc++6

---

### Post by sir-marky on 2014-06-22
So if I am interpreting your answer correctly, there are no errors but only warnings.  If so, how do I modify my command to remove those?

---

### Post by mc4man on 2014-06-22
> **sir-marky said:**
> So if I am interpreting your answer correctly, there are no errors but only warnings.  If so, how do I modify my command to remove those?
That would seem to be a new question (& there are others who may know how 'fine' logging can be adjusted with either avconv or ffmpeg.
It would appear ffmpeg suppresses some warnings or info by default, ex. with -loglevel verbose then you'd get more like avconv, except these are green  - 
> [wav @ 0x2c52d00] parser not found for codec pcm_s16le, packets or times may be invalid.
    Last message repeated 1 times
[wav @ 0x2c52d00] max_analyze_duration 5000000 reached at 5015510 microseconds


The 2nd one up the line from default in ffmpeg (info)  is -loglevel error which may give you less than you wish..
In general don't see these message(s) as any issue for most use cases, as far as " occasional artifacts within them that give the impression of those old fashioned LP things" a sample of the .wav that shows this when converted would be useful

---

