---
title: "ogg theora to ogg vorbis"
date: 2008-02-28
forum: Multimedia Production
---

### Post by crazyelf on 2008-02-28
I'm attempting to convert a .ogg file which contains both audio and video to a .ogg with only audio.  I've searched high and low. But I can't seem to find anything on this.   When searching I seem to get combining ogg theora with a sound file.  But I want to remove the sound only, and make it its own .ogg   Is this possible?

Any help would be greatly appreciated.

Aaron

---

### Post by Creative2 on 2008-02-28
you can find many command line on fuoco tools, see my signature 

from terminal 

**extract video **
```

ffmpeg -i INPUT  -an -vcodec copy -y  OUTPUT.ogg
```
[B]
extract only audio [/B]

```
ffmpeg -i INPUT  -vn -acodec vorbis -ab 128k -y OUTPUT.ogg
```

*note
it should work for every formats

---

### Post by crazyelf on 2008-02-28
I tried that, but it came out with an error.  :(
```
aaron@saturn:~$ ffmpeg -i dare_you_to_move.ogg -vn -acodec vorbis -ab 128k -y dare_u_2_move.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
[theora @ 0xb7e59ac8]Theora bitstream version 30200
[theora @ 0xb7e59ac8]584 bits left in packet 81
[theora @ 0xb7e59ac8]7 bits left in packet 82
Input #0, ogg, from 'dare_you_to_move.ogg':
  Duration: 00:04:00.2, start: 0.458594, bitrate: 422 kb/s
  Stream #0.0: Video: theora, yuv420p, 320x240, 30.00 fps(r)
  Stream #0.1: Audio: vorbis, 22050 Hz, mono, 30 kb/s
Output #0, ogg, to 'dare_u_2_move.ogg':
  Stream #0.0: Audio: vorbis, 22050 Hz, mono, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
[vorbis @ 0xb7e59ac8]Current FFmpeg Vorbis encoder only supports 2 channels.
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

I tried changing -ab 128k to  -ab 30k  like the input file... But, no luck with that either...

Thanks,

Aaron

---

### Post by Creative2 on 2008-02-28
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads 
--enable-libvorbis --enable-libtheora

you have compiled your ffmpeg , or you have installed ffmpeg that supports only free formats,  
from terminal 

**extract video **
```

ffmpeg -i INPUT  -an -vcodec copy -y  OUTPUT.ogg
```
[B]
extract only audio [/B]

```
ffmpeg -i INPUT  -vn -acodec copy  OUTPUT.ogg
```

or if you want change bitrate , you must do 


```
ffmpeg -i INPUT  -vn -acodec libvorbis -ab 128k -ac 2  -y OUTPUT.ogg
```

if doesn't work plz install ffmpeg form medibuntu repo you can find usefull link on  my signature

---

### Post by crazyelf on 2008-02-28
Thanks a lot!  You've been a great help.

Thanks again, 

Aaron

---

### Post by crazyelf on 2008-02-29
Actually... maybe not solved... it says libvorbis can't be found.  I went to their website.  Compiled it from source, because I couldn't find it as a package.  But... It still didn't work... any ideas?

Thanks,

Aaron

---

### Post by Creative2 on 2008-02-29
you have to learn about medibuntu repository ...it's easy and the fastest way to have mencoder and ffmpeg with support for every formats...

anyway to find out easly encoder you ccan do this :


ffmpeg -formats 2>&1 |grep vorbis 

you will get some thing like that 
[B]
  EA    libvorbis[/B]
 DEA    vorbis

or 

**  EA    vorbis**
 DEA    vorbis

E= encoder 

so the name of the codec to use will be 

libvorbis 

or in the second case

vorbis



if doesn't work i have no idea of what you have done, so resinstall ffmpeg from medbuntu repo.. try to use command lines i have writtten before

---

### Post by eye208 on 2008-02-29
[http://packages.ubuntu.com/gutsy/oggz-tools](http://packages.ubuntu.com/gutsy/oggz-tools)

Make sure the universe repository is enabled in software sources. Then enter
```
sudo apt-get install oggz-tools
```
to install the package. To extract the vorbis stream from a theora/vorbis .ogg file, enter
```
oggzrip -c vorbis -o audio.ogg yourvideo.ogg
```

---

### Post by Creative2 on 2008-02-29
why i must use that stuff when ffmpeg do that !?

---

### Post by eye208 on 2008-02-29
> **Creative2 said:**
> why i must use that stuff when ffmpeg do that !?
Because ffmpeg doesn't do it right.

---

### Post by Creative2 on 2008-02-29
here it worked always fine , you must install properly or from medibuntu repo..

---

### Post by eye208 on 2008-02-29
> **Creative2 said:**
> here it worked always fine , you must install properly or from medibuntu repo..
There is a bug in ffmpeg's ogg demuxer. This is unrelated to patent-encumbered codecs, so Medibuntu won't help here.

---

### Post by philc on 2008-02-29
> **eye208 said:**
> There is a bug in ffmpeg's ogg demuxer. This is unrelated to patent-encumbered codecs, so Medibuntu won't help here.

Is the problem in the Ogg muxer or demuxer?

There was a new Ogg muxer for FFmpeg completed in December 2007, removing the reliance on libogg.

---

### Post by eye208 on 2008-02-29
It's easy to find out if the bug has been fixed. Just try to demux the audio stream from "Experience Ubuntu.ogg" into a separate ogg file.
```
ffmpeg -i ~/Examples/Experience\ ubuntu.ogg -vn -acodec copy audio.ogg
```
It's giving me errors, and the output file is shorter than oggzrip's one.

libogg is the reference implementation issued by xiph.org. I don't see how reliance on it could be a mistake. oggzrip uses it too of course.

---

### Post by Creative2 on 2008-02-29
if you get error it doesn't mean  it doesn't work i have just recorded wth recordmydesktop and i have extracted ogg without error ...
i have installed this too
 libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tool
but i think you have a bad ffmpeg...
cheers

---

### Post by eye208 on 2008-02-29
> **Creative2 said:**
> i think you have a bad ffmpeg
I think you used yours on a different input file. ;)

---

### Post by crazyelf on 2008-02-29
> **eye208 said:**
> It's easy to find out if the bug has been fixed. Just try to demux the audio stream from "Experience Ubuntu.ogg" into a separate ogg file.
```
ffmpeg -i ~/Examples/Experience\ ubuntu.ogg -vn -acodec copy audio.ogg
```
It's giving me errors, and the output file is shorter than oggzrip's one.

libogg is the reference implementation issued by xiph.org. I don't see how reliance on it could be a mistake. oggzrip uses it too of course.

Exactly!!!! that's what wouldn't work for me.  I thought it was just me or something I was doing wrong.  But just incase I added the medibuntu to my repository list.  Now i'm going to install what you've suggested.  Thanks a lot for your help!

@Creative2  I reinstalled the ffmpeg from the medibuntu repository several times as well as everything listed as far as codecs that had an upgrade sign by it in synaptics I upgraded.   When converting from ogg with theora to just an ogg vorbis file the audio was trash, and it had several errors on it.  So unless its corrupt several times in a row fresh installs after removing it then readding it... that method isn't going to work.  Now from ogg to mp3 that worked like a charm.

Thanks again guys,

Aaron

---

### Post by philc on 2008-02-29
> **eye208 said:**
> It's easy to find out if the bug has been fixed. Just try to demux the audio stream from "Experience Ubuntu.ogg" into a separate ogg file.
```
ffmpeg -i ~/Examples/Experience\ ubuntu.ogg -vn -acodec copy audio.ogg
```
It's giving me errors, and the output file is shorter than oggzrip's one.


So, I've tried to do some more investigation on this. I didn't seem to have the Experience ubuntu.ogg file on my Ubuntu Studio system, so I downloaded it from here:

[https://launchpad.net/ubuntu/gutsy/+source/example-content/26](https://launchpad.net/ubuntu/gutsy/+source/example-content/26)

Then using FFmpeg please see results below:
> 
phillc@phillc-laptop:~/Desktop/example-content-26$ ffmpeg -i Experience\ ubuntu.ogg -vn -acodec vorbis experiencetest.ogg
FFmpeg version SVN-r11813, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libtheora --enable-liba52 --enable-libdc1394 --enable-libgsm --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264 --enable-shared
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb  2 2008 18:56:48, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
[theora @ 0xb7e19db0]Theora bitstream version 30200
[theora @ 0xb7e19db0]584 bits left in packet 81
[theora @ 0xb7e19db0]7 bits left in packet 82
Input #0, ogg, from 'Experience ubuntu.ogg':
  Duration: 00:01:36.8, start: 0.000000, bitrate: 295 kb/s
    Stream #0.0: Video: theora, yuv420p, 360x288 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: vorbis, 22050 Hz, stereo, 45 kb/s
Output #0, ogg, to 'experiencetest.ogg':
    Stream #0.0: Audio: vorbis, 22050 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=     379kB time=96.7 bitrate=  32.1kbits/s    
video:0kB audio:319kB global headers:3kB muxing overhead 17.723846%

As you can see no errors, but I have specified the audio codec as Vorbis.

The output file sounds fine, it is 1.36 long, which is the same as the input file.

However, using the exact command you've suggested, just copying the audio codec doesn't work:
> 
phillc@phillc-laptop:~/Desktop/example-content-26$ ffmpeg -i Experience\ ubuntu.ogg -vn -acodec copy experiencetest2.ogg
FFmpeg version SVN-r11813, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libtheora --enable-liba52 --enable-libdc1394 --enable-libgsm --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264 --enable-shared
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb  2 2008 18:56:48, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
[theora @ 0xb7d9bdb0]Theora bitstream version 30200
[theora @ 0xb7d9bdb0]584 bits left in packet 81
[theora @ 0xb7d9bdb0]7 bits left in packet 82
Input #0, ogg, from 'Experience ubuntu.ogg':
  Duration: 00:01:36.8, start: 0.000000, bitrate: 295 kb/s
    Stream #0.0: Video: theora, yuv420p, 360x288 [PAR 1:1 DAR 5:4], 25.00 tb(r)
    Stream #0.1: Audio: vorbis, 22050 Hz, stereo, 45 kb/s
Output #0, ogg, to 'experiencetest2.ogg':
    Stream #0.0: Audio: vorbis, 22050 Hz, stereo, 45 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
error, non monotone timestamps 10590 >= 10590
av_interleaved_write_frame(): Error while opening file
phillc@phillc-laptop:~/Desktop/example-content-26$ 

So, the desired output can be achieved by specifying the audio codec, rather than just copying existing.

---

### Post by eye208 on 2008-02-29
> **philc said:**
> So, the desired output can be achieved by specifying the audio codec, rather than just copying existing.
Yes, except for the fact that this is _not_ the desired output. The goal was to demux the audio stream and copy it to a separate ogg container unmodified. Re-encoding not only takes much longer but also degrades the quality of the stream.

---

