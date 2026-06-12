---
title: "Convert video to Flash"
date: 2008-01-03
forum: Multimedia Production
---

### Post by webdesigncompany on 2008-01-03
Hello,

Is there some way that i can convert video files to flash movies like those in YouTube?

---

### Post by tgilber1 on 2008-01-03
Have you looked at ffmpeg

To see available formats

ffmpeg -formats  #E encode #D decode capability

---

### Post by Creative2 on 2008-01-03
fuoco tools (interface )

or :

terminal ( i think you can change audio bitrate and video bitrate as you want )

ffmpeg -i INPUT -b 400k -r 30 -ab 128k -ar 48000 -s 320x240 OUTPUT

---

### Post by webdesigncompany on 2008-01-03
Thanks i will try theese now

---

### Post by Creative2 on 2008-01-03
ups sorry for error 

ffmpeg -i INPUT -b 400k -r 30 -ab 128k -ar 48000 -s 320x240 OUTPUT.FLV

you can write this too to force flv format 

ffmpeg -i INPUT -b 400k -r 30  -ab 128k -ar 48000 -s 320x240 -f flv OUTPUT.FLV

---

### Post by citizen_k60 on 2008-04-02
> **webdesigncompany said:**
> Hello,

Is there some way that i can convert video files to flash movies like those in YouTube?

You can try Macvide VideoFlash Converter.
It convert most of the formats to flash. You can easily convert you video files and put it on You Tube. 
See some descriptions here :

[http://www.macvide.com/Macvide_VideoFlash_Converter/]("http://www.macvide.com/Macvide_VideoFlash_Converter/")

---

### Post by sharris203 on 2008-04-10
> **Creative2 said:**
> ups sorry for error 

ffmpeg -i INPUT -b 400k -r 30 -ab 128k -ar 48000 -s 320x240 OUTPUT.FLV

you can write this too to force flv format 

ffmpeg -i INPUT -b 400k -r 30  -ab 128k -ar 48000 -s 320x240 -f flv OUTPUT.FLV

This works for me however there is no sound. Is there a way to fix this?

---

### Post by Creative2 on 2008-04-10
have you compiled ffmpeg?

i have alwyas used that command line but maybe is better put resampling from 48000 to 44100

anyway if you have not sound there is a problem with flac encoder so with ffmpeg

---

### Post by linux4me on 2008-04-13
> **Creative2 said:**
> anyway if you have not sound there is a problem with flac encoder so with ffmpeg

I don't mean to hijack this thread, but I am trying to convert some mpg's to flash using ffmpeg, and I'm running into the same problem; the videos convert, but have no sound even though the original mpg's DO have sound. I don't understand your suggestion (above). Can you clarify?

Here's the output of my comand:
> :~/Desktop$ ffmpeg -i Boag002.mpg Boag002.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mpeg, from 'Boag002.mpg':
  Duration: 00:00:48.4, start: 0.213367, bitrate: 4241 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
Output #0, flv, to 'Boag002.flv':
  Stream #0.0: Video: flv, yuv420p, 720x480, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame= 1469 q=31.0 Lsize=    2150kB time=49.0 bitrate= 359.4kbits/s    
video:2127kB audio:0kB global headers:0kB muxing overhead 1.087580%


It appears ffmpeg is trying to convert the audio but there are 0kb of audio at the end.

What do I need to do to get the audio working?

---

### Post by Creative2 on 2008-04-14
your ffmpeg is not correct i can see from here 

configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 
--disable-debug --enable-shared --prefix=/us

you have not all encoder ....


RESOLUTION

-TURN ON MEDIBUNTU REPOSITORY AND UPGRADE FFMPEG

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


or you could use mencoder

mencoder INPUT -of lavf  -oac mp3lame -lameopts abr:br=128 -srate 22050 -ovc lavc  -lavcopts vcodec=flv:vbitrate=500:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale -zoom -xy 320 -o OUTPUT.flv

---

### Post by eye208 on 2008-04-14
> **webdesigncompany said:**
> Is there some way that i can convert video files to flash movies like those in YouTube?
By the way, Flash 9.0 can also play any kind of H.264 video with AAC sound in MP4 or MOV (Quicktime) containers. The quality/size ratio of these is much better than FLV. YouTube also uses this format now. Appending "&fmt=18" to the URL of a recently uploaded YouTube video will display the MP4 version (with stereo sound!) instead of the classic FLV variant.

---

### Post by DexterLB on 2008-04-14
I use KDEnlive ( sudo apt-get install kdenlive ). It's like windows movie maker and supports lots of output formats, including flv

---

### Post by linux4me on 2008-04-14
> **Creative2 said:**
> your ffmpeg is not correct i can see from here 

configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 
--disable-debug --enable-shared --prefix=/us

you have not all encoder ....


RESOLUTION

-TURN ON MEDIBUNTU REPOSITORY AND UPGRADE FFMPEG

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Thanks!

That worked for me. What I did to get sound working with ffmpeg was:
[LIST=1]
[*]Remove ffmpeg using Synaptic.
[*]Removed all the residual and orphaned files that left behind.
[*]Used the instructions from the post you listed to add the Medibuntu repository.
[*]Reinstalled ffmpeg.
[/LIST]

Now I've got sound in my converted files. Thanks again!

---

### Post by linux4me on 2008-05-21
I just upgraded from Gutsy to Hardy, and my ffmpeg sound was gone again. 

I removed ffmpeg using Synaptic, added the Mediubuntu repositories, then installed ffmpeg.

My configuration looks like this:
> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)


I am getting this error:
> [aac @ 0xb7e2a9a8]FAAD library: libfaad.so.0 could not be opened! 
libfaad.so.0: cannot open shared object file: No such file or directory


I looked in Synaptic and found libfaad, which wasn't installed, so I installed it, but then I got the error:
> [aac @ 0xb7e179a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!


Am I missing some other library? How do I fix this?

Edit: I think I figured out what the source of this error is. I was trying to convert an *.mov to an *.flv. When I used a *.wmv instead, I was able to do the conversion without any errors.

---

### Post by Creative2 on 2008-05-21
mm i have heard something about this problem on updated system...
i am on hardy and it works fine anyway you aren't missing library it looks like there is ome problem** with** the library...

try use mencoder with this

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts vcodec=flv:vbitrate=700:acodec=libmp3lame:abitrate=192  -af lavcresample=44100 -ofps 30 -o OUTPUT

not tested...

---

### Post by linux4me on 2008-05-21
Didn't have mencoder, so I installed it using apt-get install, then ran the command you suggested and received the following output:
> MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (Family: 15, Model: 107, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Error parsing option on the command line: -lavcopts

Exiting... (error parsing command line)


---

### Post by Creative2 on 2008-05-22
:( i have left a space.. near 192 
 this is correct 

```
mencoder  INPUT -oac lavc -ovc lavc -of lavf -lavcopts vcodec=flv:vbitrate=700:acodec=libmp3lame:abitrate=128 -ofps 30 -srate 44100  -o /tmp/OUTPUT.flv
```

---

### Post by linux4me on 2008-05-22
Looks like that does the trick. It's too bad I couldn't get ffmpeg to work with the *.mov's. I really like ffmpeg...

Thanks for the help.

---

### Post by Creative2 on 2008-05-22
well i am using ffmpeg and it works but i have installed hardy from zero

---

### Post by linux4me on 2008-05-22
> **Creative2 said:**
> well i am using ffmpeg and it works but i have installed hardy from zero

Hmmm...

Do you have libfaad or libfaac installed on your machine? It seems like I am missing some library, but libfaad doesn't seem to solve the problem. 

Unfortunately, I deleted that *.mov so I no longer can test.

---

### Post by Creative2 on 2008-05-22
i only install ffmpeg from medibuntu that's all...but you are not alone for that problem , maybe is an updating issue form gutsy to hardy i don't know

---

