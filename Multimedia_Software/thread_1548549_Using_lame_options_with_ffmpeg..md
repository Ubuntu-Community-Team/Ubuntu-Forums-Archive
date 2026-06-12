---
title: "Using lame options with ffmpeg."
date: 2010-08-08
forum: Multimedia Software
---

### Post by ron999 on 2010-08-08
Hi
When using libmp3lame with ffmpeg is there a way to use lame options?:confused:
```
ffmpeg -i foo -acodec libmp3lame foo.mp3
```
For example:- --vbr-new, --abr <bitrate>, -V (n) and -q <arg>

I think it is possible to pipe ffmpeg to lame then use the options.
But is it possible to do it without a pipe.
```
ffmpeg -i foo -f wav - | lame --vbr-new -V 4 - foo.mp3
```

---

### Post by mc4man on 2010-08-08
> is there a way to use lame options

I don't think so, you'd need to use ffmpeg options, to whatever extent.
I believe you could get a vbr with -aq [COLOR="Blue"]n[/COLOR], probably close the the -V [COLOR="Blue"]n[/COLOR]

I'd just pipe to lame instead
(is there a reason you don't wish to?

---

### Post by ajgreeny on 2010-08-08
Use ```
ffmpeg -i file.wav -acodec libmp3lame -ab 128k file.mp3
``` To convert audio wav file to mp3.

-acodec is the audio codec libmp3lame.
-ab is audio bitrate.

But that may not be quite what you are asking.

---

### Post by ron999 on 2010-08-08
Thanks mc4man
(The reason for not using a pipe is because I want to make some bespoke pre-sets for WinFF)

Yes, you are correct.:D:D
Using **-aq n** seems to give vbr.
I converted the same file with lame and ffmpeg to compare and contrast.

Using these comands:-
```
lame -q 0 -V 0 foo.wav testlame.mp3
ffmpeg -i foo.wav -acodec libmp3lame -ab 320k -aq 0 testffmpeg.mp3
```

The results look very similar:-

> 
Complete name                    : testlame.mp3
Format                           : MPEG Audio
File size                        : 5.37 MiB
Duration                         : 3mn 9s
Overall bit rate                 : 238 Kbps
Writing library                  : LAME3.98r

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Duration                         : 3mn 9s
Bit rate mode                    : Variable
Bit rate                         : 238 Kbps
Minimum bit rate                 : 32.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : **5.37** MiB (100%)
Writing library                  : LAME3.98r
Encoding settings                : -m j -V 0 -q 0 -lowpass 19.5 --vbr-new -b 32

> Complete name                    : testffmpeg.mp3
Format                           : MPEG Audio
File size                        : 5.54 MiB
Encoding settings                : Lavf52.78.0

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Bit rate mode                    : **Variable**
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : **5.54** MiB (100%)


---

### Post by mc4man on 2010-08-08
> ffmpeg -i foo.wav -acodec libmp3lame [COLOR="Red"]-ab 320k[/COLOR] -aq 0 testffmpeg.mp3

I'd think you could remove that, sort of at odds with vbr, though possibly ffmpeg ignores it

---

### Post by ron999 on 2010-08-08
Yes the result is the same without **-ab 320k**.

---

### Post by andrew.46 on 2010-08-28
Hmmmm.... so I presume that lame -q 0 to -q 9 is equivalent to FFmpeg -aq 0 to -aq 9? I guess if I was not so naturally lazy I would grab a wav file and test this myself :). Nice if there were some decent documentation of this sort of feature...

Andrew

---

### Post by mc4man on 2010-08-28
> so I presume that lame -q 0 to -q 9 is equivalent to FFmpeg -aq 0 to -aq 9? 
Never really tested here either - I wouldn't be surprised if they diverge a bit. i remember once seeing some docu on it, though at the time the option didn't work so well (or at all, I forget.

Ot
What's an alt. method, though certainly of limited value with all the alternatives, is to use named pipes with mplayer to convert to mp3 w/lame.  what i used  it for wmal > flac, wmal > mp3
( though it is interesting, when doing as a 'batch named pipes' conversion, to see it work -

---

