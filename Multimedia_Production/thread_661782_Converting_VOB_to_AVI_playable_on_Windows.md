---
title: "Converting VOB to AVI playable on Windows"
date: 2008-01-08
forum: Multimedia Production
---

### Post by lduperval on 2008-01-08
Hi,

I asked this on the avidemux forum also, but since there seems to be less activity there, I'll ask here also:

I have a VOB file which says it is MPEG video, NTSC 4:3 (8:9), AC3 audio, 32000/256 kbps, Freq: 48000Hz.

I need to convert this to a file that is playable on Windows. I tried converting it (using 2.3) on a Linux machine. I tried AVI/Xvid4/Mp3 but that plays audio without video. I tried FLV/Xvid3/Mp3 and MPEG/MPEG2/MP2(Twolame) but both complain that the audio needs to be 44.1KHz (or 22 or 11).

I tried converting on a Windows machine (using 2.4), but I get the same results. I don't know what to do now.

I can play the AVI files perfectly well on Linux. If it matters any, I am also shrinking the file from 1GB to about 100 MB (by removing some of the data and by specifying a file size).

Thanks,

L

---

### Post by njparton on 2008-01-08
You need something to convert the AC3 sound (5.1 surround sound or better) to 2 channel stereo capable of being stored as mp3 etc.

You might find something out there that can do this and the video in one go, otherwise convert the sound seperately to the video and then recombine later.

---

### Post by lduperval on 2008-01-08
Uhm..... Ok. Does the fact that I can get audio to play without displaying video indicate that I am converting the AC3 correctly? Also, video **and** audio work well on Linux. It's just on Windows that it doesn't play correctly.

L

---

### Post by njparton on 2008-01-08
You may not have the correct codec installed in windows.

"AVI" is just a wrapper and inside the video and audio can be encoded with all sorts of codecs such as xvid, divx etc etc.

There's a great little free windows program called gspot (yes really) that will tell you which codecs the file is encoded with and whether you have anything installed that will decode them.

---

### Post by eye208 on 2008-01-08
Without additional codecs or players, Windows will not play anything except WMV, MPEG-1 and some very old, very bad codecs that no one is using any more.

Xvid has been a popular codec on Windows for a while, so I guess it is your best option for compatibility. The other option is Quicktime-compatible H.264 which will also give you better quality/size ratio than Xvid. But in this case the container will not be AVI but MP4.

---

### Post by philc on 2008-01-08
Do you need the video to play only on your machine or on "any" Windows machine?

If only on yours, then you have a wide range of choices if you're willing to install additional codecs.

My personal choice would be to install QuickTime 7, which includes an H.264 decoder, and encode your file using x264.

If you want it to play on "any" windows machine, then your best/only choice for maximum compatibility is probably MPEG1, as eye208 pointed out above. I don't know of any Linux encoder that will produce newer versions of Windows Media (Windows Media 9 using VC-1), but I'd love someone to tell me one was available!

For transcoding the file from MPEG to AVI, have a look at FFMPEG or Mencoder. When configuring FFMPEG,install liblame-dev and use the --enable-libmp3lame option for MP3 encoding. ([http://slashdot.org/~PhillC/journal/190344](http://slashdot.org/~PhillC/journal/190344))

There are various GUI tools out there that can be used for controlling FFMPEG/Mencoder - WinFF, ConvertIT, Fuoco (look for the threads in this forum). You could also write a command line script to control FFMPEG. I have a Bash one here - [http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode](http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode) and as an exercise have written the same thing in Perl if you're interested.

---

### Post by Creative2 on 2008-01-08
First ensure you have installed some codec pack for Windows...like k-lite or something like that 
then 


FIRST ENABLE MEDIBUNTU REPO, INSTALL FFMPEG AND MENCODER FROM THAT REPO AND THEN :

PAL(europe)
```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -o OUTPUT
```

NTSC
```
mencoder INPUT -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -o OUTPUT
```

if you like gui 


:) easy Just install this(linux)

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by njparton on 2008-01-08
If you're using vista there's a program called "vista codecs" that installs and configures a bunch of codecs for you.  Google it.

There may also be something similar for XP.

---

### Post by eye208 on 2008-01-08
IMHO codec packs on Windows are a shortcut to disaster.

But then again, it's Windows, so why should we care? :mrgreen:

---

