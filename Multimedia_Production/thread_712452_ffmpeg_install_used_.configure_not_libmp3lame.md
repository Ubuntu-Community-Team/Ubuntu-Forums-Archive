---
title: "ffmpeg install used ./configure not libmp3lame"
date: 2008-03-01
forum: Multimedia Production
---

### Post by flebber on 2008-03-01
I have installed ffmpeg both from the medibuntu repositories and from the instructions here [https://wiki.ubuntu.com/ffmpeg]("https://wiki.ubuntu.com/ffmpeg") following both methods it shows. However it seems I cannot get past the "Unknown codec 'libmp3lame'" error.

I am sort of out of ideas. This is the line I using to test ffmpeg.
```
ffmpeg -i /home/flebber/Tovid/meg11-001.vob -f mpeg -vcodec h264 -b 800k -g 300 -bf 2 -acodec libmp3lame -ab 128k /home/flebber/Tovid/trial.mpg                       
``` This is the output from it.
```
flebber@flebber-desktop:~$ ffmpeg -i /home/flebber/Tovid/meg11-001.vob -f mpeg -vcodec h264 -b 800k -g 300 -bf 2 -acodec libmp3lame -ab 128k /home/flebber/Tovid/trial.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from '/home/flebber/Tovid/meg11-001.vob':
  Duration: 00:04:34.8, start: 0.158111, bitrate: 6311 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 9800 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 224 kb/s
Unknown codec 'libmp3lame'
flebber@flebber-desktop:~$          
```

Any Ideas ? I am using kubuntu.

---

### Post by Creative2 on 2008-03-01
ffmpeg -formats 2>&1 | grep mp3 

it shound show   which encoder you must use 

E = encoder 
D = decoder

---

### Post by Sami_Sdata on 2008-03-01
[http://www.medibuntu.org](http://www.medibuntu.org) has packages with mp3 support.  I believe they have a nice walkthrough on installing it as well.

---

### Post by Sami_Sdata on 2008-03-01
Sorry, just reread your message and you are using the medibuntu package.  Let me drink some more coffee and take another look.

---

### Post by flebber on 2008-03-01
> **Creative2 said:**
> ffmpeg -formats 2>&1 | grep mp3 

it shound show   which encoder you must use 

E = encoder 
D = decoder
```

flebber@flebber-desktop:/usr/local/lib$ ffmpeg -formats 2>&1 | grep mp3
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
 DE mp3             MPEG audio layer 3
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
flebber@flebber-desktop:/usr/local/lib$   
```



You are right Creative2 I can just change to ```
ffmpeg -i /home/flebber/Tovid/meg11-001.vob -f mpeg -vcodec h264 -b 800k -g 300 -bf 2 -acodec mp3 -ab 128k /home/flebber/Tovid/trial.mpg

``` and it does work I was using libmp3lame as thats what I found on ffmpeg wiki.

# Just for reference if it helps someone

I also tried doing this ```
export LD_LIBRARY_PATH=/usr/bin/lame; /usr/bin/ffmpeg
``` idea from [http://bogdan.org.ua/categories/nix]("http://bogdan.org.ua/categories/nix")but that didn't allow it too work either.

Also used this how-to [http://symbiotix.net/node/35]("http://symbiotix.net/node/35")
but wasn't able to get that working apparently needed to > open up the FFMPEG Settings, under the ffmpeg command, I had to replace -acodec mp3 with -acodec libmp3lame from [http://www.travistidwell.com/node/263]("http://www.travistidwell.com/node/263") but I couldn't figure that out.

Anyway got it working using mp3 so thats cool thanks all.

---

### Post by Creative2 on 2008-03-02
the issue is this :

if you compile your ffmpeg many encoders have different name if you look at medibuntu's ffmpeg 

i have written about this on a topic about  aac but  this can be done for every codec and so understand what kind of ffmpeg you have and if you can encode or not

**how to check you version of ffmpeg and so understand if you CAN encode and HOW encode **

execute in a terminal this :  ```
ffmpeg -formats |grep aac:
```

-IF YOU HAVE  FFMPEG WITH NO SUPPORT FOR AAC : you will get


```

D aac ADTS AAC
```

here you** can't** see  E= encoder  so untill you have not ffmpeg with all supports you will not able to encode because you HAVE NOT Encoder 

easy solutions 

READ THIS [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29)
if you turn on medibuntu repo and update ffmpeg and mencodder will be updated and will support every formats 
[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)





-IF YOU HAVE   FFMPEG COMPILED  FROM SOURCE you will get

as you can see  here  it has D= decoder (aac) and it has  E= encoder ,name of the codec for compiled ffmpeg is libfaac 

```
 D  aac             ADTS AAC
  EA    libfaac
 D A    mpeg4aac
```

so you need to use

ffmpeg -i INPUT -ab 128k -acodec libfaac OUTPUT


 

- IF YOU HAVE   FFMPEG FROM MEDIBUNTU REPO you will get  

```

D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac

```

so you need  to use

 ffmpeg -i INPUT -ab 128k  -acodec aac OUTPUT



cheers
:popcorn:

---

