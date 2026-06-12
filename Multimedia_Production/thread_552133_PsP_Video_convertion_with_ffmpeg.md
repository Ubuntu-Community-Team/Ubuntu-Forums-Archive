---
title: "PsP Video convertion with ffmpeg"
date: 2007-09-16
forum: Multimedia Production
---

### Post by ema on 2007-09-16
Hello, I'd like to know if there's a chance to convert a video to PsP format using ffmpeg.

I'd like to convert to x264/aac.
My current PsP has 2.71 firmware and the version of ffmpeg is:
[i] FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
[/i]

I've tried to convert with h264 codec but my PsP states: "incompatible data".

Does anyone has any solution?
I'd like to not change the firmware of my PsP.

Thanks,
Ema.

Ps. I'm able to get Xvid4 movies up n running on my PsP but they're very slow (like if my PsP is missing frames while i reproduce those movies...).

---

### Post by stmiller on 2007-09-16
```

sudo apt-get install avidemux

```

This program lets you open an existing movie and save it to PSP or any other specs. You can alter settings at will as desired.

---

### Post by dvdgorila on 2007-09-17
you might have to patch the mp4 using an app called ATOM Changer, its for windows though :(

---

### Post by vinutux on 2007-09-19
use a wonderfull program called "winff" (frontend of ffmpeg)

it is in [http://biggmaatt.com/winff]("http://biggmaatt.com/winff")

it is usefull for psp:popcorn:

---

### Post by Teefs on 2007-09-26
If you want to use ffmpeg, you also might want to take a look at this: [COLOR="Blue"][http://ffmpeg.mplayerhq.hu/faq.html#SEC19]("http://ffmpeg.mplayerhq.hu/faq.html#SEC19")[/COLOR]

---

### Post by prasanthan on 2007-09-27
If anyone to help me to download this software link thanks

---

### Post by Mickeysofine1972 on 2007-09-28
i used this one and its great:

[http://pspvc.sourceforge.net](http://pspvc.sourceforge.net)

Only problem is you have to compile install it :-(

So here goes:
1) get the zip for pspvc and extract it to you home folder.

2) install the needed libs and compile the support files:

```
sudo aptitude install nasm libfaac libfaac-dev libxvidcore libxvidcore-dev liba52 liba52-dev gtk+2.0-dev build-essential
```

before installing pspvc you will need these installed/compiled so follow the guide on this link:

[http://can.homeunix.org/sw/psp/ffmpeg_psp/](http://can.homeunix.org/sw/psp/ffmpeg_psp/)

Download all the files to your home folder and open a terminal/konsole , the commands for the terminal are there on the page linked so just cut/paste into the terminal.

4) Go to the unzipped pspvc folder and type:
```
sudo sh install.sh
```

Depending on how fast you system is it will take a few minutes and then you should have a fully working Video to .MP4 converter that can do h.264 too XD

:guitar:

Mike

I'm not sure where it put the launcher icon, but it might be in sound & video

---

### Post by aspora.isernia on 2007-11-23
> **vinutux said:**
> use a wonderfull program called "winff" (frontend of ffmpeg)

it is in [http://biggmaatt.com/winff]("http://biggmaatt.com/winff")

it is usefull for psp:popcorn:

I was able to install winff, but I'm currently unable to configure it properly to convert video for my psp. Could you, please, help me?
Which conversion type do you set?
Many thanks

a.i :)

---

### Post by Creative2 on 2007-11-24
well we use mencoder instead of ffmpeg

so if you can use it :(NB MENCODER 2006 FROM REPO MEDIBUNTU)
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT
```

see this converter 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by .Ix on 2007-11-24
does anyone experience EXTREMELY long conversion times with PSPVC? i mean, i loaded this 1 hour long video and it gave me an estimated finish time of 21 hours. holy jesus. 

and avidemux doesn't give me PSP compatible files even after i rename the files properly. there's no thumbnail file too. 

this is still one of those things i go to windows for, unfortunately.

---

### Post by Creative2 on 2007-11-25
have you tried mencoder? have suggested to many people to use mencoder and it worked

```
mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT
```

unluckly now mencoder is upgrating and so that command line could not work...

so if you have mencoder 2000-2006 it will workì fine  if you have not try this 
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT
```

or 
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT
```

if you have many files to convert use this interface 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by aspora.isernia on 2007-11-25
> **.Ix said:**
> does anyone experience EXTREMELY long conversion times with PSPVC? i mean, i loaded this 1 hour long video and it gave me an estimated finish time of 21 hours. holy jesus. 

and avidemux doesn't give me PSP compatible files even after i rename the files properly. there's no thumbnail file too. 

this is still one of those things i go to windows for, unfortunately.

Wow!! PspVC is not sooo long... :D
Usually my Pspvc makes much faster conversion!!
I suggest you to select the mpeg 4 coder (not high quality h264 that cannot be enjoyed on the small screen of our PSP): it is much faster and quality is impressive!! Actually, it depends also by your machine: faster CPU means shorter encoding.
I never received 21 hours of estimated finish time...
Bye

a.i

---

### Post by aspora.isernia on 2007-11-25
> **vinutux said:**
> use a wonderfull program called "winff" (frontend of ffmpeg)

it is in [http://biggmaatt.com/winff]("http://biggmaatt.com/winff")

it is usefull for psp:popcorn:

FYI, I was able to obtain conversions for PSP with those 2 presets for WinFF, to be added in ~/.winff/presets:
```

<x264HQPSP>
    <label>H.264 High Quality (4:3) for PSP</label>
    <params>-r 29.97 -vcodec h264 -s 640x480 -aspect 4:3 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 112k -ar 48000 -ac 2 -s 480x272 -aspect 4:3</params>
    <extension>mp4</extension>
  </x264HQPSP>
  <iPodXviDPSP>
    <label>XviD for PSP (4:3)</label>
    <params>-r 29.97 -vcodec xvid -s 640x480 -aspect 4:3 -maxrate 1500k -b 1250k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec aac -ar 48000 -ab 80k -ac 2 -s 320x240</params>
    <extension>mp4</extension>
  </iPodXviDPSP>

``` 

bye
a.i

---

### Post by .Ix on 2007-11-25
> **aspora.isernia said:**
> Wow!! PspVC is not sooo long... :D
Usually my Pspvc makes much faster conversion!!
I suggest you to select the mpeg 4 coder (not high quality h264 that cannot be enjoyed on the small screen of our PSP): it is much faster and quality is impressive!! Actually, it depends also by your machine: faster CPU means shorter encoding.
I never received 21 hours of estimated finish time...
Bye

a.i

yeah i don't know man, the same video takes 40 minutes to encode on windows, with H264. :l

---

