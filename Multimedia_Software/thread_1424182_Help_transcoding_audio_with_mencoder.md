---
title: "Help transcoding audio with mencoder"
date: 2010-03-07
forum: Multimedia Software
---

### Post by ChildOfMana on 2010-03-07
Hi,

I'm trying to convert a video in .ogm format to .avi format so I can stream it to my PS3 via uShare. I'm using Mencoder and the following command to do it (to transcode the audio from vorbis to mp3 and the video from mpeg4 to xvid):

```
mencoder input.ogm -oac mp3lame -ovc xvid -xvidencopts pass=1 -o output.avi
```

The only problem is, the video contains 2 audio streams - one Japanese and one English. Needless to say, I need the English one. The above command only seems to transcode the Japanese audio though!

Here's what ffmpeg has to say about the input file:

```
Input #0, ogg, from 'input.ogm':
  Duration: 00:24:16.12, start: 0.000000, bitrate: 1280 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 576x432, 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, s16, 128 kb/s
    Stream #0.2: Audio: vorbis, 48000 Hz, stereo, s16, 192 kb/s
```

Anyone know what I can do to specify the correct audio stream to encode? Also, how can I keep the bitrate the same as the output.avi seems to default to 96kbps?

I'm not sure which audio stream is which but a little trial and error will sort that out in no time.

Thanks in advance.

---

### Post by andrew.46 on 2010-03-07
Hi ChildOfMana,

If you are keen to use MEncoder try running your file with *mplayer -v* and you will see the audio IDs printed off early in the piece. These can be selected by MEncoder by specifying the required audio ID with *-aid <ID>* on the commandline (where <ID> is the number identified by MPlayer). For better video quality rather than specify a bitrate perhaps try *vqscale=3* or consider 2 pass encoding with a fixed video bitrate...

Mind you I switched to FFmpeg a while back after using MEncoder for a long time and I have found FFmpeg easier to use and producing better results.

Andrew

---

### Post by ChildOfMana on 2010-03-07
[quote="andrew.46"]For better video quality rather than specify a bitrate perhaps try vqscale=3 or consider 2 pass encoding with a fixed video bitrate...[/quote]

Sorry man, my mistake - I should have specified I meant the audio bitrate. The video bitrate stays the same and the quality is just as good as that on the input file. The audio, on the other hand (aside form being Japanese instead of English!!), seems to default to 96kbps. I'd like to keep the original 128 (or 192 - depending on which stream is which) kbps if possible.

Thanks for the tip regarding mplayer - worked like a charm. The streams are *-aid 0* and *-aid 1* so I'll have a play round tomorrow and see if I can figure out which one is which.

---

### Post by andrew.46 on 2010-03-07
Hi ChilfOfMana,

> **ChildOfMana said:**
> The audio, on the other hand (aside form being Japanese instead of English!!), seems to default to 96kbps. I'd like to keep the original 128 (or 192 - depending on which stream is which) kbps if possible.

I should have realised as you would have been very unhappy with video at 96k :). Options can be passed to lame in the following manner:

```
-oac mp3lame **[COLOR="Red"]-lameopts xxx:xxxx:xxx[/COLOR]**
```

with whatever settings you are after, these are given in some detail in the MPlayer man pages under *lameopts*, I will admit that I have not used these options for long enough to not really know what the best ones would be :). 

> Thanks for the tip regarding mplayer - worked like a charm. The streams are *-aid 0* and *-aid 1* so I'll have a play round tomorrow and see if I can figure out which one is which.

The  can be played and thus identified by MPlayer in the following manner:

```
$ mplayer -aid 0 input_file -vo null
```


All the best,

Andrew

---

### Post by ChildOfMana on 2010-03-08
Excellent. problem solved :)

Thanks a lot for all the help :KS

---

### Post by FakeOutdoorsman on 2010-03-08
For reference a similar command using FFmpeg using the *-map* option to select the desired video and audio streams.  I added *-qscale 4* to give better output video quality than the default setting of *-b 200k*.
```
ffmpeg -i input.ogm -acodec libmp3lame -ab 192k -map 0:0 -map 0:2 -qscale 4 out.avi
```
Note that you may have to enable the mp3 encoder in FFmpeg:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by ChildOfMana on 2010-03-10
Thanks  FakeOutdoorsman.

I've got a few of these files to convert so I'll give that command a go on the next one and see how it turns out.

Thanks to both of you for your input.

---

### Post by Atilana on 2010-03-10
Hey thank you for the info, guys i like those forums, aree very useful

---

