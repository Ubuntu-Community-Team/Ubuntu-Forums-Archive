---
title: "Converting Sony OMA music files to MP3"
date: 2009-10-05
forum: Multimedia Software
---

### Post by Stosskraft on 2009-10-05
Is there an easy way of managing the music files on my Sony walkman flash MP3 player on Ubuntu? It's an NW-E005. It only seems to work with the SonicStage software, which is only available for Windows (and I do not want the hassle of running a Windows emulator like wine if I can avoid it). I've had a scoot around Google but can't find anything that works.

Also I can copy the file from the walkman, in OMA format, is there a player or file converter that works with this format? I have tried to play with a couple media players, VLC and Rythembox but no sucess.

Any ideas?

Thank you

---

### Post by andrew.46 on 2009-10-07
Hi Stosskraft,

> **Stosskraft said:**
>  OMA format, is there a player or file converter that works with this format? I have tried to play with a couple media players, VLC and Rythembox but no sucess.

You might be in a little trouble there as I believe these files are in fact ATRAC3 files that have had some DRM extras added in. A current MPlayer will play atrac3 files but the DRM additions might very well cause a problem. I do note however that FFmpeg appears to have a decoder:


```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -formats | grep oma[/COLOR]**
FFmpeg version SVN-r20110, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct  1 2009 11:11:30 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libgsm 
--enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"] D  oma             Sony OpenMG audio[/COLOR]**


```

which could very well mean that FFmpeg may be able to convert these files. Can you post a sample file somewhere?

All the best,

Andrew

---

### Post by Stosskraft on 2009-10-07
Hello Andrew, thank you for taking the time to answer. I am not sure how to go about what you suggested. I have installed the FFmpeg in the terminal but I dont have a front end to work it.

And yes your right it is ATRAC3 files.

How should I proceed now?

Thank you

---

### Post by andrew.46 on 2009-10-07
Hi Stosskraft,

> **Stosskraft said:**
>  I have installed the FFmpeg in the terminal but I dont have a front end to work it.

FFmpeg is a commandline program but pretty easy to use. If you have the repository version it will be a little limited and not allow mp3 transcoding. Have a quick look here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and you will see how to easily enable this. When this is done run the following command:

```
ffmpeg -formats | grep oma
```

as I am not entirely sure if the repository FFmpeg has the appropriate decoder, my own copy does because it is the current svn...

I have spotted a couple of .oma files on the [MPlayer samples page ]("http://samples.mplayerhq.hu/")so I shall download these and have a look after work this morning.

Andrew

---

### Post by andrew.46 on 2009-10-07
Hi Stosskraft,

I have had a look at the .oma files on the MPlayer samples page and as I feared the problem appears to be the DRM that has been inflicted on them. Under FFmpeg:

```

andrew@skamandros~/Desktop$ ffmpeg -i 03-Exdous.oma 
FFmpeg version SVN-r20110, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct  1 2009 11:11:30 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug
 --enable-shared --disable-static --enable-postproc --enable-avfilter
 --enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libgsm 
--enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
[B][COLOR="Red"][oma @ 0x806a420]Encrypted file! Eid: 1
03-Exdous.oma: Error while opening file[/COLOR][/B]


```

and then under MPlayer:

```

andrew@skamandros~/Desktop$ mplayer 03-Exdous.oma 
MPlayer SVN-r29756-4.3.3 (C) 2000-2009 MPlayer Team

Playing 03-Exdous.oma.
Seek failed
libavformat file format detected.
[B][B][COLOR="Red"][oma @ 0x8ffe8b0]Encrypted file! Eid: 1
LAVF_header: av_open_input_stream() failed[/COLOR][/B][/B]


Exiting... (End of file)

```

So I suspect that with these particular files with this type of DRM silliness, you will not be able to convert them with standard Linux tools. The good news is that I have been wrong before and hopefully this is another one of those times :).

Andrew

---

### Post by Stosskraft on 2009-10-11
*bump* (are bumps allowed?)

---

