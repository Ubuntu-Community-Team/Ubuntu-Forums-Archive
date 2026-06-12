---
title: "Can't play downloaded Google Video"
date: 2009-04-20
forum: Multimedia Software
---

### Post by afrodeity on 2009-04-20
I have downloaded two google videos with an mp4 extension. They won't play and don't appear to be corrupted. I keep getting this message: unable to determine stream or Could not determine type of stream when using totem or mplayer

I have all the medibuntu codecs installed and have tried to convert using winff

Get this message when trying to convert - could not find codec parameters.

It is probably something to do with the iPod/PSP format, but I did this a while ago and it played fine in windows.

How do I convert this type of mp4 or make it playable in Ubuntu Hardy 64?

---

### Post by paul.gevers on 2009-04-20
> **afrodeity said:**
> I have all the medibuntu codecs installed and have tried to convert using winff

If you press the play button in winff, does it play? If not it is unlikely you can convert it using winff.

However, we would be more likely to be able to help if you also include the (complete) output of winff (the console window) when you try to convert, usually there is a lot of useful information there.

---

### Post by afrodeity on 2009-04-20
Keep forgetting I can do this. Opened it in terminal using winff, then tried to play, I get this:


TGtk2WSCustomListBox.SetBorder TODO
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
/media/Gaia/Downloads/video.mp4: could not find codec parameters


Converting doesn't seem to give anything in the terminal, just a pop-up box that has some interesting info, but no way of capturing the data. I've retyped it for the sake of argument.

FFmpeg version SVN-rUNKNOWN, copyright etc
configuration --enable-gpl --enable-pp --enable-swscaler --enable-pthreads -- enable-libvorbis --enable-libtheora --enable libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
libavutil version: 1d:49.3.0
libavcodec version 1d.51.38.0
libavformat version 1d.51.10.0
built on Mar 17 2009

Does any of this make any sense to you?

---

### Post by andrew.46 on 2009-04-21
Hi afrodeity,

FFmpeg can examine the file from the commandline which should give you the output that paul.gevers mentioned, unfortunately the output you gave was incomplete. Can you open the file from the commandline as follows:

```
ffmpeg -i myfile.mp4
```

and of course substitute 'myfile.mp4' for the actual name of your file and then post the *full* terminal output here? Is it possible as well that you could give the address on the Internet where you downloaded the 2 files?

All the best,

Andrew

---

### Post by afrodeity on 2009-04-21
Well at least I know how to get this all done in the terminal; here is the output, not much different.

```

afrodeity@afrodeity-desktop:/media/Gaia/Downloads$ ffmpeg -i video.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
video.mp4: could not find codec parameters

```

Oh, and before I forget, the download link from video.google.com was 

[http://v17.lscache7.googlevideo.com/videoplayback?id=5e0dd1cacf08e73a&itag=7&begin=0&ratebypass=yes&title=Discovery_Channel_-_The_History_Of_Hacking_Documentary.avi&ip=0.0.0.0&ipbits=0&expire=1240329034&sparams=ip,ipbits,expire,id,itag,ratebypass,title&signature=79EBE63C64CEAD29A4EBED94F5C927A1552E0A1A.2B581BCFF00354EB159ACCB843CD75847D378A16&key=ck1](http://v17.lscache7.googlevideo.com/videoplayback?id=5e0dd1cacf08e73a&itag=7&begin=0&ratebypass=yes&title=Discovery_Channel_-_The_History_Of_Hacking_Documentary.avi&ip=0.0.0.0&ipbits=0&expire=1240329034&sparams=ip,ipbits,expire,id,itag,ratebypass,title&signature=79EBE63C64CEAD29A4EBED94F5C927A1552E0A1A.2B581BCFF00354EB159ACCB843CD75847D378A16&key=ck1)

---

### Post by paul.gevers on 2009-04-21
> **afrodeity said:**
> 
video.mp4: could not find codec parameters


Googling a little bit it looks like the error means that you have to specify the dimensions. Not sure thou, so I will test tonight.

[Thread about YUV with same error.]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-February/006763.html")

---

### Post by andrew.46 on 2009-04-21
Hi afrodeity,

> **afrodeity said:**
> Oh, and before I forget, the download link from video.google.com was 

[http://v17.lscache7.googlevideo.com/videoplayback?id=5e0dd1cacf08e73a&itag=7&begin=0&ratebypass=yes&title=Discovery_Channel_-_The_History_Of_Hacking_Documentary.avi&ip=0.0.0.0&ipbits=0&expire=1240329034&sparams=ip,ipbits,expire,id,itag,ratebypass,title&signature=79EBE63C64CEAD29A4EBED94F5C927A1552E0A1A.2B581BCFF00354EB159ACCB843CD75847D378A16&key=ck1](http://v17.lscache7.googlevideo.com/videoplayback?id=5e0dd1cacf08e73a&itag=7&begin=0&ratebypass=yes&title=Discovery_Channel_-_The_History_Of_Hacking_Documentary.avi&ip=0.0.0.0&ipbits=0&expire=1240329034&sparams=ip,ipbits,expire,id,itag,ratebypass,title&signature=79EBE63C64CEAD29A4EBED94F5C927A1552E0A1A.2B581BCFF00354EB159ACCB843CD75847D378A16&key=ck1)

Big download :-). Alter the ending and it works with MPlayer and FFmpeg. Instead of '.avi.mp4' alter it to '.mp4' and the contents show as:

```

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Discovery_Channel_-_The_History_Of_Hacking_Documentary.mp4':
Duration: 00:50:09.12, start: 0.000000, bitrate: 365 kb/s
Stream #0.0(und): Video: h264, yuv420p, 320x232, 29.97 tbr, 29.97 tbn, 59.94 tbc
Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16

```

Might be an excellent idea to transcode it as it seems to have something of a dual personality avi / mp4. A quick screenshot of this long clip playing...

Andrew

---

### Post by afrodeity on 2009-04-21
> **andrew.46 said:**
> Hi afrodeity,



Big download :-). Alter the ending and it works with MPlayer and FFmpeg. Instead of '.avi.mp4' alter it to '.mp4' and the contents show as:


Might be an excellent idea to transcode it as it seems to have something of a dual personality avi / mp4. A quick screenshot of this long clip playing...

Andrew

Already is .mp4. ffmpeg is installed. How to transcode?

---

### Post by andrew.46 on 2009-04-21
Hi afrodeity,

> **afrodeity said:**
> Already is .mp4. ffmpeg is installed. How to transcode?

But the final few letters of the file I downloaded were actually '.avi.mp4'. Is this not the case with your file? I had to drop either '.avi' or '.mp4' to play the file.

Once you can play the file you should be able to convert using winFF, I noted that your copy of FFmpeg is set up for x264 and aac which are the contents of this file.

All the best,

Andrew

---

### Post by afrodeity on 2009-04-23
Trying to see if mencoder can deal with the problem. Otherwise I give up. File must be corrupted or something. Thanks for the help anyway.

---

