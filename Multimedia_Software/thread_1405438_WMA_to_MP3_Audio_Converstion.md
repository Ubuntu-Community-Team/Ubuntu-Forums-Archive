---
title: "WMA to MP3 Audio Converstion"
date: 2010-02-12
forum: Multimedia Software
---

### Post by Zylstra555 on 2010-02-12
Hello, 

I would like to know how I can best convert my WMA audio files to MP3. 

I do not wish to use OGG. The device which has caused my need to convert file formats does support OGG, but even OGG has so many variations that, from what I read, it is far to problematic. The device (a Sansa Fuze) will support MP3 files much better. 

Someone recommended using the FFMPEG command, however I was not able to get it to work (I think they may have given me the wrong syntax). 

If a file is already in Mp3 format, I don't want a converter program to run it through again. A program that will not change specified file types would be nice. 

Desperation: This issue is causing me to want to move back to Windows (Oh No!)

---

### Post by andrew.46 on 2010-02-12
Hi Zylstra,

> **Zylstra555 said:**
> Someone recommended using the FFMPEG command, however I was not able to get it to work (I think they may have given me the wrong syntax).

FFmpeg is a great tool for this sort of work. Can you post the command suggested to you + the complete terminal output? This should give a hint as to why the transcode failed.

All the best,

Andrew

---

### Post by Zylstra555 on 2010-02-12
Command: ffmpeg -i "$i" "${i%wma}mp3";
Output:

jessezylstra@jessezylstra-laptop:~/Music/Downloaded Music$ ffmpeg -i "$i" "${i%wma}mp3";
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
: no such file or directory

---

### Post by SuperSonic4 on 2010-02-12
Have you tried using ffmpeg on just one file, to test if it work?

Soundconverter will also do the job. My personal preference is pacpl, a kde app although you may be able to compile w/o dolphin/amarok/konqueror support

---

### Post by Zylstra555 on 2010-02-12
SoundConverter tries to redo my existing MP3 files, and I would use it anyways, but it just stopped working one day. Restarting SoundConverter did not help. 

I do not know how to use the FFMPEG command line tool.

---

### Post by SuperSonic4 on 2010-02-12
WinFF is a GUI for ffmpeg

```
ffmpeg -i input.wma output.mp3
```

where input and output are obvious

---

### Post by Zylstra555 on 2010-02-12
Hey, I figured out what was going on with SoundConverter. Stupidly, the folder I was trying to convert was full of only mp3 files that it had already converted. 

Now, I have another problem: SoundConverter is not keeping the ID3 tag data, I am not sure why. I am loosing song titles, artists, and all that jazz.

---

### Post by ajgreeny on 2010-02-12
I think you may need the unstripped versions of libavcodec, libavformat and libavutils to encode mp3s.  They can be decoded, but not encoded if you have the normal versions, if I remember correctly.

---

### Post by andrew.46 on 2010-02-12
Hi Zylstra,

> **Zylstra555 said:**
> 
```
: no such file or directory
```


Perhaps as Supersonic has suggested you could try a *single* file rather than a whole directory of files as your syntax suggests you are attempting. The error indicates there are no wma files to process in this location BTW. Better still could you interrogate one of these wmas as follows:

```
ffmpeg -i my_file.wma
```

substituting the *actual* name of the file for *my_file.wma*. If you post the full command + terminal output this may prove helpful.

Andrew

---

### Post by VastOne on 2010-02-12
> **Zylstra555 said:**
> Hey, I figured out what was going on with SoundConverter. Stupidly, the folder I was trying to convert was full of only mp3 files that it had already converted. 

Now, I have another problem: SoundConverter is not keeping the ID3 tag data, I am not sure why. I am loosing song titles, artists, and all that jazz.

You will most likely need to use EasyTAG to re tag your wma files. I just went through this converting all my wma to flac and had to use EasyTAG

---

### Post by lucasart on 2010-02-13
1/ You must have ffmpeg installed. To see if you have it, just type
```

ffmpeg

```If it doesn't recognize the command, then install it by typing
```

sudo get-apt install ffmpeg

```2/ Encoding a single file (change the 128k to whatever bitrate you prefer)
```

ffmpeg -i input.wma -acodec mp2 -ab **128k** output.mp3

```3/ Encoding a directory tree using a find loop (extremely powerful Unix command)
```

find /home/user/Music/ -iname \*.wma -type f -exec ffmpeg -i {} -acodec mp2 -ab **128k** {}.mp3 \;

```For your understanding, "-type f" filters files only, "{}" is the loop variable (ie filename matching the criterion -iname \*.wma). If you only want the current directory and no subdirectories, stick a "-maxepth 0" before "-exec".

And by the way to delete your original *.wma files, use another find loop!
```

find /home/user/Music/ -iname \*.wma -type f -exec rm {} \;

```

PS: why would you want to convert *.wma to *.mp3 ??? Going from a compressed format to another compressed format looses further quality. In other words you'll get a worst quality/size ratio by doing WMA -> MP3, than by doing PCM/WAV/FLAC -> MP3. Besides, MP3 compression is clearly not as good as WMA or AAC. Anyway, that is your choice...

---

