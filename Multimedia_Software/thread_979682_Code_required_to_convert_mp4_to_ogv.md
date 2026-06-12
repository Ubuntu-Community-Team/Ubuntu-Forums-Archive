---
title: "Code required to convert mp4 to ogv"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Rytron on 2008-11-12
Hi,
I need to convert mp4 to ogv using mencoder or ffmpeg.
I tried oggconvert but it did not work for this particular mp4 file.
Thanks.

---

### Post by FakeOutdoorsman on 2008-11-12
Generally, "ffmpeg input ouput.ogg" will work, but by default, for some unknown reason, ffmpeg will use FLAC instead of vorbis for audio with OGG container, so vorbis must be specified:
```
ffmpeg -i kideatsdirt.mp4 -acodec vorbis -vcodec libtheora kideatsdirt.ogv
```

---

### Post by Rytron on 2008-11-12
> **FakeOutdoorsman said:**
> Generally, "ffmpeg input ouput.ogg" will work, but by default, for some unknown reason, ffmpeg will use FLAC instead of vorbis for audio with OGG container, so vorbis must be specified:
```
ffmpeg -i kideatsdirt.mp4 -acodec vorbis -vcodec libtheora kideatsdirt.ogv
```

Output:

```
:~/Desktop$ ffmpeg -i a.mp4 -acodec vorbis -vcodec libtheora a.ogv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'a.mp4':
  Duration: 00:21:35.1, start: 0.000000, bitrate: 492 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 352x264 [PAR 0:1 DAR 0:1], 25.00 tb(r)
    Stream #0.1(und): Audio: mp3, 22050 Hz, stereo, 128 kb/s
Unable to find a suitable output format for 'a.ogv'
```

---

### Post by FakeOutdoorsman on 2008-11-12
Curse these multiple ffmpeg versions!  Try this:
```
ffmpeg -i a.mp4 -acodec vorbis -vcodec libtheora -f ogg a.ogv
```
Your version seems like it doesn't know what ogv is, so it has to be told with "-f ogg".  This code will use the default bitrate of 200k, so you may want to increase that with "-b 512k" or whatever.  Same for audio, default is 64k, so change it with "-ab 128k".

---

### Post by Rytron on 2008-11-24
Hi,
I tried 
```
ffmpeg -i a.mp4 -acodec vorbis -vcodec libtheora -f ogg a.ogv 
```
but no luck.

Then I tried ```
ffmpeg -i a.mp4 -b 1024k -acodec vorbis -vcodec libtheora -f ogg a.ogv
```
Both methods recorded the full length and the sound was perfect. However the video was garbled.

What I did in the end was converted the file using Media Coder in Windows and then converted the file from avi to ogv using OGGConvert in Ubuntu.
Done.

Edit: Granted, I could have converted the mp4 file to an avi file in Ubuntu. It would still be preferable to have a method to do it in Mencoder or FFmpeg though.

---

### Post by Rodnox on 2010-02-06
Using WIndows is no solution for me. Anybody got an update on that?

Need to convert ogv to mpeg or mp4. VLC won't work. Avidemux doesn't recognize ogv files.

i'm stuck.

---

### Post by amsterdamharu on 2010-02-06
> Using WIndows is no solution for me.

You can try VLC to re-encode but it doesn't do a good job. Probably need to re-encode the result with Avidemux

---

### Post by Rytron on 2010-02-06
> **Rodnox said:**
> Using WIndows is no solution for me. Anybody got an update on that?

Need to convert ogv to mpeg or mp4. VLC won't work. Avidemux doesn't recognize ogv files.

i'm stuck.

Try devede.

---

### Post by cor2y on 2010-02-06
what does ffmpeg -formats | grep ogg display?
I can convert to ogv easily with ffmpeg but i am using the latest svn build r21651

---

### Post by SuperSonic4 on 2010-02-06
> **cor2y said:**
> what does ffmpeg -formats | grep ogg display?
I can convert to ogv easily with ffmpeg but i am using the latest svn build r21651

r21658 is the latest revision ;) but I get your point

The below worked fine but surely x264 is a better encoder?

```
ffmpeg -i /mnt/Videos/Music\ Videos/When\ The\ Tigers\ Broke\ Free\ \(Video\).mov -vcodec libtheora -acodec libvorbis -ab 128k -b 350k ~/Tigers.ogv
```

---

### Post by Rodnox on 2010-02-06
VLC is crap for converting, it never gets the right codecs. I know, i could manually ajust them, but there are other programs that can fetch them automatically, so I kinda expect that from a program in 2010. 

I found a Program, that converts and comes with all the required plug-ins and Codecs. 

WinFF it's called. Don't ask me why it's called so, it aint got nothing to do with windows. 

Can be installed via Synaptic.

---

### Post by SuperSonic4 on 2010-02-06
> **Rodnox said:**
> VLC is crap for converting, it never gets the right codecs. I know, i could manually ajust them, but there are other programs that can fetch them automatically, so I kinda expect that from a program in 2010. 

I found a Program, that converts and comes with all the required plug-ins and Codecs. 

WinFF it's called. Don't ask me why it's called so, it aint got nothing to do with windows. 

Can be installed via Synaptic.

**Win**dow (ie GUI)
**FF**mpeg (the backend it's based on)


WinFF is simply a frontend to FFmpeg and it is an excellent tool for those more comfortable with a GUI than the CLI

---

### Post by Railsbuntu on 2010-07-29
Hi,

I can't convert mp4 video to ogv using ffmpeg 0.5.x, any idea what's the correct syntax to use?

---

### Post by ron999 on 2010-07-29
> **Railsbuntu said:**
> Hi,

 any idea what's the correct syntax to use?

Hi
Use the syntax:-
```
ffmpeg -i foo.mp4 foo.ogg
```

If it doesn't work for you then go back and read through the whole thread.

---

### Post by davidmaxwaterman on 2011-05-25
I have had success with a utility called 'ffmpeg2theora' (though that is on fedora so I don't know if there is such a package for ubuntu.

---

### Post by Rytron on 2011-05-25
> **davidmaxwaterman said:**
> I have had success with a utility called 'ffmpeg2theora' (though that is on fedora so I don't know if there is such a package for ubuntu.

You can get [COLOR="Indigo"]ffmpeg2theora[/COLOR] from [COLOR="DarkOrange"]Synaptic Package Manager[/COLOR] in Ubuntu.

---

