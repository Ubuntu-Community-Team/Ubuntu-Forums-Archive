---
title: "Audio DVD PCM: 48 kHz or 96 kHz sampling rate, 16 bit or 24 bit Linear PCM, 2 ch"
date: 2014-06-08
forum: Multimedia Software
---

### Post by valeriancafe on 2014-06-08
Hello and good day to One and All,

My goal using Ubuntu 14.04 command line is to try and make a Audio DVD  [COLOR="#FF0000"]( Not DVD-A ) [/COLOR]from my flac music. I up-sampled from 16 bits to 24 bits

1) DVD spec PCM: 48 kHz or 96 kHz sampling rate, 16 bit or 24 bit Linear PCM, 2 channels = 4608 kb/s found info online

2) found this code to convert from flac to wav here on this nice forms " for f in *.flac; do sox  "$f" -b 24 -r 44100  ./resampled/"${f%.flac}.wav"; done "

File Size: 108M      Bit Rate: 2.12M <----------------------- How can I get the bit rate to 4608 kb/s ??????
Encoding: Signed PCM    
Channels: 2 @ 24-bit   
Samplerate: 44100Hz      
Replaygain: off         
Duration: 00:06:48.24
3) I would like to make my on music compilations. I need program that I can loop the background, picture not a video in the Video_TS folder and my music would go in the Audio_TS folder

4) then burn in Nero Linux

---

### Post by tgalati4 on 2014-06-09
Was your source music "SuperAudio CD"?  Why would you waste space by upscaling your music from 16-bits to 24-bits?  That will take up a lot of space.  

Try the command above using 96000 instead of 44100 for the rate switch.  That will get you 96 kHz sampling instead of 44,100 Hz sampling.

96/44.1=2.177 and 2.177*2.12 Mbits/sec= 4.615 Mbits/sec.

For making a video, look at *openshot*.  I don't know if an Audio DVD format can handle a looping picture--I'm not familiar with the format.

---

### Post by Bucky Ball on 2014-06-09
Sample rate/bit rate should be same as the original. You can't improve the audio quality of the original. That's it.

---

### Post by Yellow Pasque on 2014-06-09
> **Bucky Ball said:**
> Sample rate/bit rate should be same as the original. You can't improve the audio quality of the original. That's it.

Yes, but DVD format calls for PCM/wav at 48 or 98 kHz, so OP needs to at least convert to wav @ 48kHz.
```
 for f in *.flac; do sox "$f" -r 48000 ./resampled/"${f%.flac}.wav"; done
```

Either that, or OP will have to convert to AC-3.

---

### Post by mc4man on 2014-06-10
You need to decide if you're going to DVD-Video  or DVD-Audio. 
For DVD-Video all the files go into a VIDEO_TS folder,  DVD-Audio uses AUDIO_TS

When I used to make dvd audio disks ( DVD-Video), I'd author as titles based on artist, album & or category. Tracks would be chapters inside those titlesets. Also  menus for navigation, ect. 
Never did so on linux because it's so easy to do on windows.

Maybe take a look here - 
[http://audioplex.sourceforge.net/](http://audioplex.sourceforge.net/)

---

### Post by valeriancafe on 2014-06-13
Thanks for Helping.... I found a code that helps me with one file for LPCM code " sox name.flac -b 24 name.wavpcm rate -v -s -I 96k " How can I do this with a holder of flac files ?:guitar:

---

### Post by tgalati4 on 2014-06-14
I don't know if *sox* accepts wildcards like *.flac, but you can try it on a test directory of files.  Otherwise, you would need to write a recursive script for going through each file in a directory.  There are numerous examples on these forums.  Search convert mp3 script.

---

### Post by tgalati4 on 2014-06-14
I don't know if *sox* accepts wildcards like *.flac, but you can try it on a test directory of files.  Otherwise, you would need to write a recursive script for going through each file in a directory.  There are numerous examples on these forums.  Search convert mp3 script.

It might look something like:

```


#!/bin/bash
# Super cheesy script to convert flac files to DVD pcm
for i in *.flac; do
     musictrack=$(ls "$i" | sed -e 's/.flac//g')
     echo "Converting:  " $musictrack
     sox "$musictrack.flac" -b 24 "$musictrack.wav" rate -v -s -I 96k
     echo "Done converting:  "  $musictrack
done
exit 0

```

---

### Post by shantiq on 2014-06-14
[COLOR=#DD4814][COLOR=#000000][valeriancafe]("http://ubuntuforums.org/member.php?u=703289") [/COLOR][/COLOR]cd to folder where your 16-bit flac files are and run

```
for f in *.flac ; do sox "$f" -b 24 -r 96k "${f%.flac}.wav" ; done
```

check with mediainfo

> mediainfo *wav
General
Complete name                            : 01 - Open Heart.wav
Format                                   : Wave
File size                                : 156 MiB
Duration                                 : 4mn 43s
Overall bit rate mode                    : Constant
Overall bit rate                         : 4 608 Kbps


Audio
Format                                   : PCM
Format settings, Endianness              : Little
Format settings, Sign                    : Signed
Codec ID                                 : 00001000-0000-0100-8000-00AA00389B71
Duration                                 : 4mn 43s
Bit rate mode                            : Constant
Bit rate                                 : **4 608 Kbps**
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : **96.0 KHz**
Bit depth                                : **24 bits**
Stream size                              : 156 MiB (100%)


General
Complete name                            : 08 - Angie La La.wav
Format                                   : Wave
File size                                : 252 MiB
Duration                                 : 7mn 37s
Overall bit rate mode                    : Constant
Overall bit rate                         : 4 608 Kbps


Audio
Format                                   : PCM
Format settings, Endianness              : Little
Format settings, Sign                    : Signed
Codec ID                                 : 00001000-0000-0100-8000-00AA00389B71
Duration                                 : 7mn 37s
Bit rate mode                            : Constant
Bit rate                                 : 4 608 Kbps
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 96.0 KHz
Bit depth                                : 24 bits
Stream size                              : 252 MiB (100%)




---

### Post by Yellow Pasque on 2014-06-14
I'm not sure why the OP is trying to convert to 24-bit. I don't think it's necessary (and it probably won't increase audio quality of a 16-bit FLAC).

---

### Post by shantiq on 2014-06-15
[FONT=arial][COLOR=#000000]Hi [Temüjin]("http://ubuntuforums.org/member.php?u=327594")[/COLOR][COLOR=#000000]  these are the specs he requested         [/COLOR]> [COLOR=#000000]1) DVD spec PCM: 48 kHz or 96 kHz sampling rate, 16 bit or 24 bit Linear PCM, 2 channels = 4608 kb/s [/COLOR]

but yes   of course    they will be "fake"  24/96    since the sound cannot be improved;   can only be put in a "wider" container    ;   i am not crystal-clear as to what he wants to make here ;    just gave him the tools to do the conversion he asked for ie   24/96 [/FONT][COLOR=#000000][I]4608 kb/s wav   ....     he may or may not need these


he says he does not want [dva-A]("https://en.wikipedia.org/wiki/DVD-Audio")   but that is the only format that would request such high specs



he probably only wants flac with an image attached so to be able to burn that to a normal dvd


[B]so


[/B]to do that:

```
sox     input1.flac input2.flac etc     final.flac
```[/I][/COLOR]    to get   all your flac files as one

then to attach image:

```
time ffmpeg  -loop 1 -r 2 -i input.png -i input.flac -c:a copy -c:v libx264 -g 7 -crf 0 -vf scale=-1:720 -preset veryfast -shortest VIDEO.mkv

```
probably 480 enough if for dvd

```
time ffmpeg  -loop 1 -r 2 -i input.png -i input.flac -c:a copy -c:v libx264 -g 7 -crf 0 -vf scale=-1:480 -preset veryfast -shortest VIDEO.mkv

```

then create a dvd iso   with **devede **  [found in synaptic]   and really easy to use and stable [click on add file and find your VIDEO.mkv] then burn iso to dvd 


[B]so did a test to check    and this is the dvd specs u end up with 

[/B]flac scaled down to 448 kbps ac3 which is the best you will get in a dvd it seems [[IMG]http://s20.postimg.org/9acgciuxl/test.jpg[/IMG]]("http://postimg.org/image/9acgciuxl/")

---

### Post by valeriancafe on 2014-06-15
Thanks for helping, I know resampling from 16 bit to 24 bits does not improve the recordings. I just need it in DVD-video specs LPCM to play on a DVD player.  Plus I know some people who would like to save their LP's so I can use sox. I looked over the ( man  sox ) pages most of it looks like rocket science.  To quote the man sox "  sox -p song.ogg silence 1 0.50 0.1% 1 2.0 0.1% : \             newfile : restart
       records  a stream of audio such as LP/cassette and splits in to multiple audio files at points with 2 seconds of silence.  Also, it does not start recording until it detects audio is playing
       and stops after it sees 10 minutes of silence. " :guitar: might have some fun.... and Thanks again ...long live linux and other Distros :P

---

