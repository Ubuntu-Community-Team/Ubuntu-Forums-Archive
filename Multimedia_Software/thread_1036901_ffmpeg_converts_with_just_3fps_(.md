---
title: "ffmpeg converts with just 3fps :("
date: 2009-01-11
forum: Multimedia Software
---

### Post by pink_fone on 2009-01-11
Hi everyone!  I use this script in converting movies for iPod:

```

for movie in *.avi ; 
do
ffmpeg -i "$movie" -f mp4 -vcodec libxvid -s 640x360 -aspect 1.77 -maxrate 1500k -b 768k -qmin 3 -qmax 5 -bufsize 4096k -mbd 2 -flags +4mv -trellis 1 -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libfaac -ab 128k -ac 2 "/media/Yang/Movies/mp4/$movie.mp4"
done

```

It used to work fine on 7.10 - 8.04.  However, now that I am using 8.10, it still converts the movie fine but more than twice slower than it used to work on 7.10-8.04.  I also noticed that it only converts at the speed of 3fps.  Does any one know where I should look to make it convert faster than 3fps?  I'm posting part of the console's output below which states that it's running at 3fps.  I think it used to be around 8fps in the previous versions of Ubuntu.

```

Press [q] to stop encoding
frame=205 fps=3 q=3.0 size=19005kB time=1.4 bitrate= 701.8kbits/s    

```

---

### Post by FakeOutdoorsman on 2009-01-12
I get about 12 fps using your command on a 3 GHz Pentium 4.  Is it slow for you if you use libx264 instead of libxvid?
```
ffmpeg -i "$movie" -vcodec libx264 -s 640x360 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 6 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -threads 0 -acodec libfaac -ab 128k -ar 48000 -ac 2 "/media/Yang/Movies/mp4/$movie.mp4"
```
You could also try compiling the most recent version of ffmpeg since development is active:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

Using a new ffmpeg would require you to edit your original command to:
```
ffmpeg -i "$movie" -f mp4 -vcodec libxvid -s 640x360 -aspect 1.77 -maxrate 1500k -b 768k -qmin 3 -qmax 5 -bufsize 4096k -mbd 2 -flags +4mv+aic -trellis 1 -cmp 2 -subcmp 2 -g 300 -acodec libfaac -ab 128k -ac 2 "/media/Yang/Movies/mp4/$movie.mp4"
```
Alternatively with a new ffmpeg you could just:
```
ffmpeg -i input.avi -f ipod output.m4v
```

---

### Post by andrew.46 on 2009-01-12
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Alternatively with a new ffmpeg you could just:

```
ffmpeg -i input.avi -f ipod output.m4v
```

I searched through the docs (man pages and html docs) and found next to nothing about 'ipod' as an encoder although it is obviously present in my copy of ffmpeg:

```
andrew@skamandros~$ ffmpeg -formats | grep ipod
FFmpeg version SVN-r16512, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-swscale 
--enable-x11grab --enable-libmp3lame --enable-libxvid --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libamr-wb 
--enable-libamr-nb --enable-nonfree --enable-gpl
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52.10. 0 / 52.10. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 10 2009 05:06:10, gcc: 4.2.4
 **[COLOR="Red"] E ipod            iPod H.264 MP4 format[/COLOR]**

```

Is there any way of finding out what the defaults are for this encoder when used as you have suggested? I can see from using it that it produces h264 video and aac audio with perfectly acceptable results but I am a little curious about the defaults chosen by the ffmpeg developers.

Now if only I actually *owned* an ipod :-).

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-01-14
> **andrew.46 said:**
> Hi FakeOutdoorsman,



I searched through the docs (man pages and html docs) and found next to nothing about 'ipod' as an encoder although it is obviously present in my copy of ffmpeg:

Is there any way of finding out what the defaults are for this encoder when used as you have suggested? I can see from using it that it produces h264 video and aac audio with perfectly acceptable results but I am a little curious about the defaults chosen by the ffmpeg developers.

Now if only I actually *owned* an ipod :-).

All the best,

Andrew

Good question.  I looked through the source, but I didn't understand it.  I've actually never used "-f ipod" besides just trying it out since I also don't own an iPod.  One of the devs said "-f ipod" may not be valid or useful anymore since it has been some time since that was created and Apple keeps changing things to keep the iPod picky.  I think it mostly just muxes the mp4 correctly so it (previously?) works with both iPod and iTunes.  Also, I think the [iPod video guide](http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/) is more up to date and probably creates better results. iDunno.

---

