---
title: "Error Converting WAV to FLAC"
date: 2008-07-10
forum: Multimedia Software
---

### Post by lightnb on 2008-07-10
I'm trying to convert .wav to .flac files using:

```

shntool conv -o flac *.wav

```

And getting the error:

```

Converting [bob.wav] (4:28.10) --> [bob.flac] :   0% ERROR
shntool [conv]: warning: error while transferring 47298720-byte data chunk -- skipping.
shntool [conv]: warning: child encoder process 9068 had non-zero exit status 1

```

---

### Post by Creative2 on 2008-07-10
add medibuntu repository to your source list 
then install ffmpeg

ffmpeg -i INPUT.wav  -ab 192k -y OUTPUT.flac

---

### Post by lightnb on 2008-07-10
Cool, thanks.

Two  questions:

I assume "-i" is the input file, and "-y" is the output file.

So the "-ab 192k" option sets the bit rate to 192k? Won't that reduce the output file's quality? What setting should you use for lossless?

Second, how can this be automated? For example, take the wav's filename and use it as the flac's name, and convert all the files in a directory and its subdirectories?

---

### Post by mc4man on 2008-07-10
I'm not 100% sure but I don't think that when converting to flac the -ab xxx matters. i did the same .wav 3 different ways (specified bitrate, no bitrate set, and with soundconverter) and they all are the same size and reported bitrate.

Edit; possibly when you specify it becomes the min. (flac seems to be vbr) doing this same output as no bitrate specified (64k)
```
doug@doug-desktop:~$ ffmpeg -i boldaslove.wav -ab 999k -y test5.flac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-x264 --enable-liba52 --enable-libmp3lame --enable-libfaac --enable-libfaad --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on May  5 2008 11:58:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, wav, from 'boldaslove.wav':
  Duration: 00:04:11.6, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, 1411 kb/s
Output #0, flac, to 'test5.flac':
  Stream #0.0: Audio: flac, 44100 Hz, stereo, 999 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   30699kB time=251.6 bitrate= 999.5kbits/s    
video:0kB audio:30699kB global headers:0kB muxing overhead 0.000025%
```

---

### Post by lightnb on 2008-07-11
I guess I'll just set it at 1411 (such an odd number...) since that's what the original files are.

Is there a way to make this function recursive, to convert all files in a directory?

---

### Post by ron999 on 2008-07-11
> **lightnb said:**
> 

Is there a way to make this function recursive, to convert all files in a directory?

I found out how to take a folder full of wav files and make FLAC versions.

Open a monitor.
Use CD to change directory to the required folder.
Enter:-
```
flac --best *
```

I got the information from this thread here:-[http://ubuntuforums.org/showthread.php?t=320351]("http://ubuntuforums.org/showthread.php?t=320351")

PS You might need to install FLAC first.
Use:-
```
sudo apt-get install flac
```

---

### Post by mc4man on 2008-07-11
> I guess I'll just set it at 1411  I think you misunderstood me, I was just making example that setting a bitrate for flac has no effect.
From flac site

> With FLAC you do not specify a bitrate like with some lossy codecs. It's more like specifying a quality with Vorbis or MPC, except with FLAC the quality is always "lossless" and the resulting bitrate is roughly proportional to the amount of information in the original signal. You cannot control the bitrate much and the result can be from around 100% of the input rate (if you are encoding noise), down to almost 0 (encoding silence).

I think Ron's method above looks best, if your going to use ffmpeg I'd specify no bitrate.

---

