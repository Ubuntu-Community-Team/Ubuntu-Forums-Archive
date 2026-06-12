---
title: "Sound Converters"
date: 2010-07-11
forum: Multimedia Software
---

### Post by tank.tmt on 2010-07-11
Hey I have been looking for a program in the software centre that will convert music files with videos into pure audio files. I have found 3 programs and heard of a 4th: Sound Converter, WinFF, Arista and the 4th is Gnormalise. I cannot figure out the differences between these though, although I did see that Gnormalise has the ability to adjust the volume recorded on a file it was not in the software centre.

So my question is what are the differences and can anyone make recommendations?
Also why isn't Gnormalise in Ubuntu's software centre?

---

### Post by sahilsameerac on 2010-07-11
you can install soun converyter from software center of can type "sudo apt-get install soundconverter" in terminal.

---

### Post by robert shearer on 2010-07-11
Soundconverter works very well for me. Recommended !

---

### Post by Linuxforall on 2010-07-11
WinFF does this with ease.

---

### Post by shantiq on 2010-07-11
soundkonverter with a k is the most versatile in your synaptic and also shntool (command line) is a must

tips to use it are

to install


```
sudo apt-get install shntool

```
Shntool functions as a frontend of sorts for lossless audio software (mac, flac, wavpack). It performs a range of functions including facilitating the conversion of music files between the various lossless formats (ape, flac, wv, wav, etc). Note that shntool has native support for .wav files only; if you want it to work with .ape, .flac or .wv files then you must have the appropriate helper programs (mac, flac, wavpack respectively) installed. For a full list of the lossless formats supported by shntool type &#8220;shntool -f&#8221;. To convert all .ape files in a directory to flac using shntool:

```
shntool conv -o flac *.ape

```
This command can also be given as:

```
shnconv -o flac *.ape

```




from the command-line also ffmpeg for video to audio

---

### Post by shantiq on 2010-07-11
also   ```
sudo apt-get install pacpl

```


```
PACPL(1)              User Contributed Perl Documentation             PACPL(1)

NAME
       pacpl - Perl Audio Converter, a multi purpose converter/ripper/tagger

SYNOPSIS
       pacpl --to <format> <options> [file(s)/directory(s)]

DESCRIPTION
       Perl Audio Converter is a tool for converting multiple audio types from
       one format to another. It supports AAC, AC3, AIFF, APE, AU, AVR, BONK,
       CAF, CDR, FAP, FLA, FLAC, IRCAM, LA, LPAC, MAT, MAT4, MAT5, M4A, MMF,
       MP2, MP3, MP4, MPC, MPP, NIST, OFR, OFS, OGG, PAC, PAF, PVF, RA, RAM,
       RAW, SD2, SF, SHN, SMP, SND, SPX, TTA, VOC, W64, WAV, WMA, and WV.  
       [B][COLOR="Blue"]It can also convert audio from the following video extensions: RM, RV,
       ASF, DivX, MPG, MKV, MPEG, AVI, MOV, OGM, QT, VCD, SVCD, M4V, NSV, NUV,
       PSP, SMK, VOB, FLV, and WMV[/COLOR][/B]. A CD ripping function with CDDB support,
       batch conversion, tag preservation for most supported formats,
       independent tag reading/writing, and extensions for Amarok, Dolphin,
       and Konqueror are also provided.


```


if you file is in your home directory and called 1.avi

```
pacpl -t wv 1.avi
```

and find your wv in your home folder


of course you have a choice of these formats/replace wv for one of those

AAC, AC3, AIFF, APE, AU, AVR, BONK,
       CAF, CDR, FAP, FLA, FLAC, IRCAM, LA, LPAC, MAT, MAT4, MAT5, M4A, MMF,
       MP2, MP3, MP4, MPC, MPP, NIST, OFR, OFS, OGG, PAC, PAF, PVF, RA, RAM,
       RAW, SD2, SF, SHN, SMP, SND, SPX, TTA, VOC, W64, WAV, WMA, and WV.

---

### Post by tank.tmt on 2010-07-11
Ok I tried Sound Converter and it often shutdown when it was performing an operation or just after it had finished one and it wasn't supposed to. So now I am trying WinFF

---

### Post by andrew.46 on 2010-08-07
Hi shantiq,

> **shantiq said:**
> shntool (command line) is a must...

I am relatively new to shntool but I have been using it over the last little while to *join* together a small library of flac files I have. A great tool well worth exploring :).

Andrew

---

### Post by Brackenn on 2010-09-20
Hi. I got a bunch of MP3's that I want to burn to a disk, for my simple in-dash, factory equipment car stereo. what is the easiest and simplest way to convert MP3 to CDR using Ubuntu?

---

### Post by garethfoxwilliams on 2010-09-20
Brasero, the default CD burner works fine. 

Just start off the project by clicking on "create and audio CD"

Let me know if you have any problems.

gareth

---

### Post by keildozer on 2011-02-15
Here i have got a question do any of these convert an MP4(audio) to MP3?:neutral: 

you see i got some songs from pandora for the tmp folder in my computer.

---

### Post by PaulReaver on 2011-02-15
I recommend sound converter

my little bro (bliss him) uses soundconverter to rip the audio from video  'aquired' using youtube-dl... the little teevin ba*d

good software...

---

### Post by PaulReaver on 2011-02-15
> **keildozer said:**
> Here i have got a question do any of these convert an MP4(audio) to MP3?:neutral: 

you see i got some songs from pandora for the tmp folder in my computer.

soundconverter will do that

---

### Post by keildozer on 2011-02-16
thanks for that i'll try that.

---

### Post by keildozer on 2011-02-17
No what I want is something that is free.
But thanks for the advice.

---

