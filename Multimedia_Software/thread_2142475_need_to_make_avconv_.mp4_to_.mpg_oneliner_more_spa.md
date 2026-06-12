---
title: "need to make avconv .mp4 to .mpg oneliner more space efficient"
date: 2013-05-05
forum: Multimedia Software
---

### Post by thaitang on 2013-05-05
I have a collection of children's vid's I got from youtube that I want to make available for my kids to watch on the home entertainment system. Unfortunately the dvd player does not recognize most of the common formats such as .mp4 or .webm or .flv. So I have been using the following command to batch convert:
```
find . -type f -name "*.mp4" -exec bash -c 'avconv -i "$0" -target ntsc-dvd -aspect 4:3 "${0/%mp4/mpg}"' '{}' \;
```
Although the videos can now be played on the home ent. dvd player, the file size is sometimes four times larger than the origonal. I expected some degree of bloat due to better compression rates with the newer codecs, but this unexpected amount is chewing through a lot of space, fast.

I have also used Arista-transcoder as an alternate method and so far the results are much better: the file size of the resulting .mpg, while larger, is only minimal. Unfortunately I do not have the time to sit and convert each of the files one at a time, since it does not look like Arista offers any sort of batch capapbility.

I started Arista (gui) from the command line, hoping to see what commands it might beissuing so I could modify the oneliner I included above, but nothing was printed back in the terminal.

Are there any other ways I could puke out what Arista is doing behind the scenes (gui) so I can incorporate it into a batch oneliner?

---

### Post by michael37 on 2013-05-05
I think the difference you see is not a tool that you are using for transcoder, but a "bitrate" transcoding setting. "-target ntsc-dvd" implies a certain high bitrate. I'd recommend to play around with "-b" option of avconv to reduce bitrate of your videos. You can also use avconv (aka ffmpeg) command to view the bitrate of Arista-transcoded videos.

For more details, see section "BASIC VIDEO TRANSCODING" of this guide: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/).

---

### Post by michael37 on 2013-05-05
Example, this file has 8k bitrate (way too high)

% avconv -i MyAristaFile.mpg
(blah blah blah)
Input #0, mpeg, from 'MyAristaFile.mpg':
  Duration: 00:00:07.90, start: 0.287267, bitrate: 8979 kb/s
    Stream #0:0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [SAR 16:15 DAR 4:3], 8000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0:1[0x80]: Audio: ac3, 48000 Hz, 5.1(side), s16, 448 kb/s

---

### Post by thaitang on 2013-05-05
> **michael37 said:**
> Example, this file has 8k bitrate (way too high)

% avconv -i MyAristaFile.mpg
...
[COLOR=#000000]Duration: 00:00:07.90, start: 0.287267, bitrate: 8979 kb/s[/COLOR]
Ok, great news that avconv can grab all the info I should need. The results I get are:
```
avconv -i *.mpgavconv version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
[mpeg @ 0x9b83240] max_analyze_duration reached
[NULL @ 0x9b857a0] start time is not set in estimate_timings_from_pts
Input #0, mpeg, from 'ABC Song in the Clouds (ZED version) - YouTube [720p].mpg':
**  Duration: 00:01:40.02, start: 1.000000, bitrate: 899 kb/s**
    Stream #0.0[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 192 kb/s
    Stream #0.1[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x406 [PAR 1:1 DAR 360:203], 4000 kb/s, 24 fps, 24 tbr, 90k tbn, 48 tbc
At least one output file must be specified
```

So I have tried to modify my oneliner, attempting to break the avconv command down to basics to begin with:
 ```
 find . -type f -name "*.mp4" -exec bash -c 'avconv -i "$0" -b 900k "${0/%mp4/mpg}"' '{}' \;
```
but I continue to get the error:
```
 [mp2 @ 0x96f2740] bitrate 900 is not allowed in mp2
 Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height
```
I based the -b 900k flag value on the 899kb/s listed by avconv's inquiry of the Arista file's .mpg. The flag value also appear consistent with examples listed in the avconv man page, so I am at a bit of a loss. I wonder if when specifying a bit rate (-b) if other specified params are req'd along with it?

any advice much appreciated.

---

### Post by thaitang on 2013-05-06
So I have tried to modify my oneliner, attempting to break the avconv command down to basics to begin with:
 ```
 find . -type f -name "*.mp4" -exec bash -c 'avconv -i "$0" -b 900k "${0/%mp4/mpg}"' '{}' \;
```
but I continue to get the error:[/QUOTE]
Ok, so that was a pretty simple fix. The video bitrate flage value does not need the k(ilobits) designation.
```
find . -type f -name "*.mp4" -exec bash -c 'avconv -i "$0" -b 900 "${0/%mp4/mpg}"' '{}' \;
```
seems to work fine now, although I have not yet tested the result on the home dvd player.

---

