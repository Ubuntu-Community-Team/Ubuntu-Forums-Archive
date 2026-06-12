---
title: "How to convert audio file of type G.723.1 into wav format using sox?"
date: 2013-06-14
forum: Multimedia Software
---

### Post by shekharkotekar on 2013-06-14
[COLOR=#000000][FONT=Arial]I have few audio files which have [/FONT][/COLOR].wav[COLOR=#000000][FONT=Arial] extension. I tried to get information about this file using [/FONT][/COLOR]soxi <foo.wav>[COLOR=#000000][FONT=Arial] command but I got following error :
[/FONT][/COLOR][INDENT]soxi FAIL formats: can't open input file foo.wav': Unknown WAV file encoding (type a100)
[/INDENT][COLOR=#000000][FONT=Arial]So I used MediaInfo tool to get more information about this file I got following information about this file:

[/FONT][/COLOR]
[INDENT]**General**
Format : Wave
File size : 51.4 KiB
Duration : 1mn 18s Overall
bit rate : 5 339 bps
**Audio**
Format : G.723.1
Codec ID : A100
Duration : 1mn 18s
Bit rate : 5 328 bps
Channel(s) : 1 channel
Sampling rate : 8 000 Hz
Stream size : 51.3 KiB (100%)
[/INDENT][COLOR=#000000][FONT=Arial]According to this information it seems like this file is has G.723.1 format and SOX is not able to understand this format.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I would like to know :[/FONT][/COLOR]

[LIST]
[*]My conclusion that SOX does not support this type of file is correct?
[*]If SOX does not support this type of file then installing some codec will help? I have seen lamecommand on few web pages but not sure if it will help me or not.
[/LIST]
Request someone to help !

---

### Post by shekharkotekar on 2013-06-14
[COLOR=#000000][FONT=Arial]I have few audio files which have [/FONT][/COLOR].wav[COLOR=#000000][FONT=Arial] extension. I tried to get information about this file using [/FONT][/COLOR]soxi <foo.wav>[COLOR=#000000][FONT=Arial] command but I got following error :
[/FONT][/COLOR][INDENT]soxi FAIL formats: can't open input file foo.wav': Unknown WAV file encoding (type a100)
[/INDENT]
[COLOR=#000000][FONT=Arial]So I used MediaInfo tool to get more information about this file I got following information about this file:

[/FONT][/COLOR][INDENT]**General**
Format : Wave
File size : 51.4 KiB
Duration : 1mn 18s Overall
bit rate : 5 339 bps
**Audio**
Format : G.723.1
Codec ID : A100
Duration : 1mn 18s
Bit rate : 5 328 bps
Channel(s) : 1 channel
Sampling rate : 8 000 Hz
Stream size : 51.3 KiB (100%)
[/INDENT]
[COLOR=#000000][FONT=Arial]According to this information it seems like this file is has G.723.1 format and SOX is not able to understand this format.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I would like to know :[/FONT][/COLOR]

[LIST]
[*]My conclusion that SOX does not support this type of file is correct?
[*]If SOX does not support this type of file then installing some codec will help? I have seen lamecommand on few web pages but not sure if it will help me or not.
[/LIST]
Request someone to help !

---

### Post by Cheesemill on 2013-06-14
Threads merged.

---

### Post by shantiq on 2013-06-14
Hi S


this is a [phone audio file]("http://voiceage.fullvu.com/g7231.php") right?

[COLOR=#000000][FONT=Verdana][LEFT]**G.723.1 — Delivering Highly Compressed Speech at Near-toll Quality **Adopted in November 1995 by the International Telecommunication Union (ITU), the G.723.1 codec can be used for compressing the speech or the audio component of multimedia services at a very low bit rate as part of the overall H.323 and H.324 families of standards.[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][LEFT]G.723.1 offers a dual rate of 6.3 kbps, based upon an MP-MLQ2 codebook search, and 5.3 kbps, based on the unique ACELP® technology platform developed at the Université de Sherbrooke. The higher bit rate has greater quality. The lower bit rate gives good quality and provides system designers with additional flexibility. Both rates are mandatory parts of the encoder and decoder. It is possible to switch between the two rates at any 30-ms frame boundary.[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][LEFT]G.723.1 can perform full duplex compression and decompression functions for multimedia, visual telephony, and videoconferencing products. It was optimized to represent speech with high quality at low bit rates using a limited amount of complexity. Music and other audio signals are not represented as faithfully as speech but can be compressed and decompressed using this coder.[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][LEFT]By delivering highly compressed speech, this codec is targeted for communications applications where low bit-rates are required without compromising the speech quality. In fact, G.723.1 provides near-toll quality.[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]**[LEFT][B]Technical Highlights**[/LEFT]
[/B][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][LEFT]
[LIST]
[*]Frame size: 30 ms (240 samples)
[*]Lookahead: 7.5 ms (60 samples)
[*]Bit rates: 5.3 & 6.3 (MOS at 6.3 is 3.9)
[*]Possibility of switching between both rates during real-time operation
[*]Optional VAD/CNG (G.723 Annex A
[/LIST]
[FONT=Verdana]
[/FONT]
[/LEFT]
[/FONT][/COLOR]could you upload a sample here for us to try?   thanx

---

### Post by Yellow Pasque on 2013-06-15
sox probably doesn't support it.

It looks like libav supports it, but you'll need a newer version  than what's in the repos.
[http://git.libav.org/?p=libav.git;a=blob;f=Changelog;hb=refs/tags/v9.6#l203](http://git.libav.org/?p=libav.git;a=blob;f=Changelog;hb=refs/tags/v9.6#l203)

It also looks like it's supported in ffmpeg. Since I use Debian, I'll leave it to the libav/ffmpeg experts to tell you the best way to go about getting the right version in Ubuntu. By the way, which version of Ubuntu are you using?

---

### Post by FakeOutdoorsman on 2013-06-15
Getting a recent build of ffmpeg has two main options:

**Static build of ffmpeg**
Pros:
[list]
[*]Simply [download, extract, and run](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453).
[*]You don't have to compile.
[/list]

Cons:
[list]
[*]May not have what you want, such as no x11 support for screen capture, and no support for non free encoders such as libfdk_aac.
[*]You don't get to compile.
[/list]

**Compile ffmpeg**
Pros: 
[list]
[*]Get the latest and greatest and can customize to your liking.
[*]There is a [step-by-step ffmpeg compile guide for Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). Just copy and paste.
[*]You get to compile.
[/list]

Cons:
[list]
[*]You have to compile.
[*]Bigger download than static build due to dependencies and sources.
[/list]

---

### Post by andrew.46 on 2013-06-15
Hmmm... love to see a sample of one of these files...

---

